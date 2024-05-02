---
title: Configurazione della connessione Adobe Commerce Intelligence per i progetti Cloud Starter esistenti
description: Questo articolo fornisce una soluzione per quando desideri configurare la connessione Adobe Commerce Intelligence per un progetto Cloud Starter esistente.
feature: Commerce Intelligence
role: Developer
exl-id: 56f6ad64-729d-4e3a-93a9-da1b91bc5c1d
source-git-commit: b75328202952bf4c8f57ddc538b5c9e4318b2001
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 0%

---

# Configurazione della connessione Adobe Commerce Intelligence per i progetti Cloud Starter esistenti

>[!NOTE]
>
>Adobe Commerce Intelligence era precedentemente nota come Magento Business Intelligence (MBI).

Questo articolo fornisce una soluzione per quando desideri configurare la connessione Adobe Commerce Intelligence per un progetto Cloud Starter esistente.

## Prodotti e versioni interessati

Adobe Commerce su cloud starter (tutte le versioni)

## Problema

Si desidera configurare la connessione Commerce Intelligence per un progetto Cloud Starter esistente.

>[!NOTE]
>
>Adobe non supporta più i nuovi abbonamenti a Cloud Starter, ma se disponi di un progetto Starter esistente, dovrai seguire i passaggi riportati di seguito per configurare la connessione.

## Soluzione

Per attivare i progetti Commerce Intelligence for Cloud Starter, crea un account Commerce Intelligence, crea una chiave SSH e infine collegati al database Adobe Commerce.

Segui questi passaggi:

1. Crea il tuo account Adobe Commerce Intelligence:

   * Vai a [accounts.magento.com/customer/account/login](https://account.magento.com/customer/account/login).
   * Accedi a **[!UICONTROL My Account]** > **[!UICONTROL My MBI Instances]**.
   * Fai clic su **[!UICONTROL Create Instance]**. Se non trovi questo pulsante, contatta il tuo Customer Success Manager o Customer Technical Advisor.
   * Seleziona l’abbonamento a Cloud Starter. Se disponi solo di un abbonamento a Cloud Starter, questo verrà selezionato automaticamente.
   * Clic **[!UICONTROL Continue]**.
   * Inserisci le informazioni per creare l’account.

   ![Crea account MBI](/help/troubleshooting/miscellaneous/assets/create_mbi_account.png)

   * Vai alla tua casella in entrata e verifica l’indirizzo e-mail.

   ![Verifica indirizzo e-mail](/help/troubleshooting/miscellaneous/assets/verify_email_address_mbi.png)

   * Creare una password.

   ![Creare una password](/help/troubleshooting/miscellaneous/assets/create_password_mbi.png)

   * Dopo aver creato l’account, avrai la possibilità di aggiungere utenti al nuovo account. È ora possibile aggiungere gli amministratori tecnici per eseguire i seguenti passaggi.

   ![Aggiungi utenti](/help/troubleshooting/miscellaneous/assets/add_users_mbi.png)

1. Inserisci informazioni sul tuo Negozio per impostare le tue preferenze.

   ![Aggiungi informazioni archivio](/help/troubleshooting/miscellaneous/assets/add_store_info_mbi.png)

   Prima di collegare il database per il terzo passaggio del flusso di onboarding è necessario raccogliere alcune informazioni. Verrà compilato il *[!UICONTROL Connect your database]* al passaggio 9.

1. Creazione di un utente Commerce Intelligence dedicato.

   * Crea un nuovo utente il [account.adobe.com](https://account.adobe.com/).
   * Vai a [https://accounts.magento.com/customer/account/](https://accounts.magento.com/customer/account/) per generare il tuo account Adobe Commerce.
   * Perché un nuovo utente? Adobe Commerce Intelligence richiede che un utente aggiunto al progetto recuperi continuamente nuovi dati da trasferire al data warehouse di Commerce Intelligence dell&#39;account. Questo utente fungerà da connessione. L’aggiunta di questo utente al progetto avverrà nel passaggio 4.
   * L&#39;utente Commerce Intelligence dedicato ha lo scopo di impedire che l&#39;utente aggiunto venga inavvertitamente disattivato o eliminato e che venga interrotta la connessione Commerce Intelligence.

1. Aggiungi l’utente appena creato all’ambiente principale del progetto come *Collaboratore*.

   ![Aggiungere un utente come collaboratore](/help/troubleshooting/miscellaneous/assets/contributor_user_mbi.png)

1. Ottenere le chiavi SSH di Commerce Intelligence.

   * Vai a **[!UICONTROL Connect your database]** dell&#39;interfaccia utente di configurazione di Commerce Intelligence e scorrere verso il basso fino a **[!UICONTROL Encryption settings]**.
   * Per il campo, **[!UICONTROL Encryption Type]**, scegli **[!UICONTROL SSH Tunnel]**.
   * Dall’elenco a discesa, puoi copiare e incollare la chiave pubblica di Magento BI Essentials fornita.

   ![Impostazioni crittografia](/help/troubleshooting/miscellaneous/assets/encryption_type_mbi.png)

1. Aggiungere la nuova chiave pubblica Magento BI Essentials all&#39;utente Commerce Intelligence creato al passaggio 5.

   * Vai a [accounts.magento.com/customer/account/login](https://account.magento.com/customer/account/login). Accedere con le informazioni di accesso dell&#39;account per il nuovo utente di Commerce Intelligence creato. Quindi vai al **[!UICONTROL Account Settings]** scheda.
   * Scorri verso il basso nella pagina ed espandi il menu a discesa per le chiavi SSH. Quindi fai clic su **[!UICONTROL Add a public key]**.

   ![Aggiungi una chiave pubblica](/help/troubleshooting/miscellaneous/assets/add_public_key_mbi.png)

   * Aggiungi la chiave pubblica SSH di Magento MBI Essentials dall’alto.

   ![Aggiungi chiave pubblica SSH](/help/troubleshooting/miscellaneous/assets/add_ssh_key_mbi.png)

1. Fornisci credenziali MySQL di Business Intelligence Essentials.

   * Aggiorna il tuo `.magento/services.yaml`.

   ```
   mysql:
    type: mysql:10.0
    disk: 2048
    configuration:
        schemas:
            - main
        endpoints:
            mysql:
                default_schema: main
                privileges:
                    main: admin
            mbi:
                default_schema: main
                privileges:
                    main: ro
   ```

   * Aggiorna il tuo `.magento.app.yaml`.

   ```
   relationships:
            database: "mysql:mysql"
            mbi: "mysql:mbi"
            redis: "redis:redis"
   ```

1. Ottenere informazioni sulla connessione del database a Commerce Intelligence.

   Esegui `echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 --decode | json_pp` per ottenere informazioni sulla connessione al database.

   Dovresti ricevere informazioni simili a quelle riportate di seguito:

   ```
   "mbi" : [
              {
                 "scheme" : "mysql",
                 "rel" : "mbi",
                 "cluster" : "vfbfui4vmfez6-master-7rqtwti",
                 "query" : {
                    "is_master" : true
                 },
                 "ip" : "169.254.169.143",
                 "path" : "main",
                 "host" : "mbi.internal",
                 "hostname" : "3m7xizydbomhnulyglx2ku4wpq.mysql.service._.magentosite.cloud",
                 "username" : "mbi",
                 "service" : "mysql",
                 "port" : 3306,
                 "password" : "[password]"
              }
           ],
   ```

1. Connetti il tuo database Adobe Commerce.

   ![Connettere il database Adobe Commerce](/help/troubleshooting/miscellaneous/assets/connect_magento_database_mbi.png)

   *Input*:

   * Nome integrazione: [Scegli un nome per l’integrazione.]
   * Host: `mbi.internal`
   * Porta: 3306
   * Nome utente: mbi
   * Password: [password di input fornita nell&#39;output del punto 8.]
   * Nome database: main
   * Prefissi tabella: [lascia vuoto se non sono presenti prefissi di tabella]

1. Imposta il [!UICONTROL Timezone Settings].

   ![Impostazioni del fuso orario](/help/troubleshooting/miscellaneous/assets/timezone_settings_mbi.png)

   *Input*

   * Database: Fuso orario: UTC
   * Fuso orario desiderato: [Scegli il fuso orario in cui visualizzare i dati.]

1. Ottieni informazioni sulle impostazioni di crittografia.

   * L’interfaccia utente del progetto fornisce una stringa di accesso SSH. Questa stringa può essere utilizzata per raccogliere le informazioni necessarie per l&#39;indirizzo remoto e il nome utente nella configurazione **[!UICONTROL Encryption settings]**. Seleziona **[!UICONTROL SSH]** per visualizzare il nome utente e l&#39;indirizzo remoto. La stringa di testo prima del *@* è il tuo nome utente e la stringa di testo dopo *@* è il tuo indirizzo remoto.

   ![Accedi a pagina mastro sito](/help/troubleshooting/miscellaneous/assets/access_site_mbi.png)

1. Informazioni di input per [!UICONTROL Encryption Settings].

   ![Impostazioni crittografia](/help/troubleshooting/miscellaneous/assets/encryption_type_mbi.png)

   *Input*

   * Tipo di crittografia: tunnel SSH
   * Indirizzo remoto: ssh.us-3.magento.cloud
   * Nome utente: vfbfui4vmfez6-master-7rqtwti—mymagento
   * Porta: 22

1. Clic **[!UICONTROL Save Integration]**.
1. Connessione all&#39;account Commerce Intelligence Essentials completata.
1. Se sei un cliente Adobe Commerce Intelligence Pro, contatta il tuo Customer Success Manager o il tuo consulente tecnico per coordinare i passaggi successivi.
