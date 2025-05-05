---
title: Configurazione della connessione Adobe Commerce Intelligence per i progetti Cloud Starter esistenti
description: Questo articolo fornisce una soluzione per quando desideri configurare la connessione Adobe Commerce Intelligence per un progetto Cloud Starter esistente.
feature: Commerce Intelligence
role: Developer
exl-id: 56f6ad64-729d-4e3a-93a9-da1b91bc5c1d
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '776'
ht-degree: 0%

---

# Configurazione della connessione Adobe Commerce Intelligence per i progetti Cloud Starter esistenti

>[!NOTE]
>
>Adobe Commerce Intelligence era precedentemente noto come Magento Business Intelligence (MBI).

Questo articolo fornisce una soluzione per quando desideri configurare la connessione Adobe Commerce Intelligence per un progetto Cloud Starter esistente.

## Prodotti e versioni interessati

Adobe Commerce su cloud starter (tutte le versioni)

## Problema

Desideri configurare la connessione Commerce Intelligence per un progetto Cloud Starter esistente.

>[!NOTE]
>
>Adobe non supporta più i nuovi abbonamenti a Cloud Starter, ma se disponi di un progetto Starter esistente, dovrai seguire i passaggi riportati di seguito per configurare la connessione.

## Soluzione

Per attivare i progetti Commerce Intelligence for Cloud Starter, crea un account Commerce Intelligence, crea una chiave SSH e infine collegati al database Adobe Commerce.

Segui questi passaggi:

1. Crea il tuo account Adobe Commerce Intelligence:

   * Vai a [accounts.magento.com/customer/account/login](https://account.magento.com/customer/account/login).
   * Passa a **[!UICONTROL My Account]** > **[!UICONTROL My MBI Instances]**.
   * Fare clic su **[!UICONTROL Create Instance]**. Se non trovi questo pulsante, contatta il tuo Customer Success Manager o Customer Technical Advisor.
   * Seleziona l’abbonamento a Cloud Starter. Se disponi solo di un abbonamento a Cloud Starter, questo verrà selezionato automaticamente.
   * Fare clic su **[!UICONTROL Continue]**.
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

   Prima di collegare il database per il terzo passaggio del flusso di onboarding è necessario raccogliere alcune informazioni. Compilerai la pagina *[!UICONTROL Connect your database]* nel passaggio 9.

1. Crea un utente Commerce Intelligence dedicato.

   * Crea un nuovo utente in [account.adobe.com](https://account.adobe.com/).
   * Vai a [https://accounts.magento.com/customer/account/](https://accounts.magento.com/customer/account/) per generare il tuo account Adobe Commerce.
   * Perché un nuovo utente? Adobe Commerce Intelligence richiede che un utente aggiunto al progetto recuperi continuamente nuovi dati da trasferire al data warehouse Commerce Intelligence dell’account. Questo utente fungerà da connessione. L’aggiunta di questo utente al progetto avverrà nel passaggio 4.
   * La presenza di un utente Commerce Intelligence dedicato ha lo scopo di impedire che l&#39;utente aggiunto venga inavvertitamente disattivato o eliminato e che venga interrotta la connessione Commerce Intelligence.

1. Aggiungi l&#39;utente appena creato all&#39;ambiente principale del progetto come *Collaboratore*.

   ![Aggiungi utente come collaboratore](/help/troubleshooting/miscellaneous/assets/contributor_user_mbi.png)

1. Ottieni le tue chiavi SSH di Commerce Intelligence.

   * Andare alla pagina **[!UICONTROL Connect your database]** dell&#39;interfaccia utente di configurazione di Commerce Intelligence e scorrere verso il basso fino a **[!UICONTROL Encryption settings]**.
   * Per il campo **[!UICONTROL Encryption Type]**, scegliere **[!UICONTROL SSH Tunnel]**.
   * Dall’elenco a discesa, puoi copiare e incollare la chiave pubblica di Magento BI Essentials fornita.

   ![Impostazioni crittografia](/help/troubleshooting/miscellaneous/assets/encryption_type_mbi.png)

1. Aggiungi la nuova chiave pubblica Magento BI Essentials all’utente Commerce Intelligence creato nel passaggio 5.

   * Vai a [accounts.magento.com/customer/account/login](https://account.magento.com/customer/account/login). Accedi con le informazioni di accesso dell&#39;account per il nuovo utente Commerce Intelligence creato. Quindi passare alla scheda **[!UICONTROL Account Settings]**.
   * Scorri verso il basso nella pagina ed espandi il menu a discesa per le chiavi SSH. Quindi fare clic su **[!UICONTROL Add a public key]**.

   ![Aggiungi una chiave pubblica](/help/troubleshooting/miscellaneous/assets/add_public_key_mbi.png)

   * Aggiungi la chiave pubblica SSH di Magento MBI Essentials dall’alto.

   ![Aggiungi chiave pubblica SSH](/help/troubleshooting/miscellaneous/assets/add_ssh_key_mbi.png)

1. Fornire le credenziali [!DNL MySQL] di Business Intelligence Essentials.

   * Aggiorna `.magento/services.yaml`.

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

   * Aggiorna `.magento.app.yaml`.

   ```
   relationships:
            database: "mysql:mysql"
            mbi: "mysql:mbi"
            redis: "redis:redis"
   ```

1. Ottenere informazioni per la connessione del database a Commerce Intelligence.

   Eseguire `echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 --decode | json_pp` per ottenere informazioni sulla connessione al database.

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

   ![Connetti il tuo database Adobe Commerce](/help/troubleshooting/miscellaneous/assets/connect_magento_database_mbi.png)

   *Input*:

   * Nome integrazione: [Scegliere un nome per l&#39;integrazione.]
   * Host: `mbi.internal`
   * Porta: 3306
   * Nome utente: mbi
   * Password: [password di input fornita nell&#39;output del passaggio 8.]
   * Nome database: main
   * Prefissi tabella: [lasciare vuoto se non sono presenti prefissi tabella]

1. Imposta [!UICONTROL Timezone Settings].

   ![Impostazioni fuso orario](/help/troubleshooting/miscellaneous/assets/timezone_settings_mbi.png)

   *Input*

   * Database: Fuso orario: UTC
   * Fuso orario desiderato: [Scegliere il fuso orario in cui visualizzare i dati.]

1. Ottieni informazioni sulle impostazioni di crittografia.

   * L’interfaccia utente del progetto fornisce una stringa di accesso SSH. Questa stringa può essere utilizzata per raccogliere le informazioni necessarie per l&#39;indirizzo remoto e il nome utente durante la configurazione di **[!UICONTROL Encryption settings]**. Selezionare **[!UICONTROL SSH]** per visualizzare il nome utente e l&#39;indirizzo remoto. La stringa di testo prima di *@* è il tuo nome utente e la stringa di testo dopo *@* è il tuo indirizzo remoto.

   ![Accedi a sito principale](/help/troubleshooting/miscellaneous/assets/access_site_mbi.png)

1. Immettere le informazioni per [!UICONTROL Encryption Settings].

   ![Impostazioni crittografia](/help/troubleshooting/miscellaneous/assets/encryption_type_mbi.png)

   *Input*

   * Tipo di crittografia: tunnel SSH
   * Indirizzo remoto: ssh.us-3.magento.cloud
   * Nome utente: vfbfui4vmfez6-master-7rqtwti—mymagento
   * Porta: 22

1. Fare clic su **[!UICONTROL Save Integration]**.
1. Connessione all&#39;account Commerce Intelligence Essentials completata.
1. Se sei un cliente Adobe Commerce Intelligence Pro, contatta il tuo Customer Success Manager o il tuo consulente tecnico per coordinare i passaggi successivi.

## Lettura correlata

[Best practice per la modifica delle tabelle del database](https://experienceleague.adobe.com/it/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) nel playbook di implementazione di Commerce
