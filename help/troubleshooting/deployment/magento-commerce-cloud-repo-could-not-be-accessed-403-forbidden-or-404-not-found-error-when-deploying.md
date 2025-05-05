---
title: "Impossibile accedere all’archivio Adobe Commerce sul cloud: errore 403 Forbidden o 404 Not Found durante la distribuzione"
description: "Questo articolo illustra come risolvere l’errore di distribuzione non riuscita di Adobe Commerce sull’infrastruttura cloud in modo simile al seguente:"
exl-id: 2f72d80a-05b2-4908-8fa8-61d06885ed07
feature: Cloud, Deploy, Paas, Variables
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '608'
ht-degree: 0%

---

# Impossibile accedere all’archivio Adobe Commerce sul cloud: errore 403 Forbidden o 404 Not Found durante la distribuzione

Questo articolo illustra come risolvere l’errore di distribuzione non riuscita di Adobe Commerce sull’infrastruttura cloud in modo simile al seguente:

&quot;*Impossibile accedere all&#39;URL &#39;https://repo.magento.com/archives/magento/magento-cloud-configuration/magento-magento-cloud-configuration-x.x.x.x.zip&#39;: HTTP/1.1 403 Forbidden* &quot;. Oppure non è stato possibile scaricare il file &quot;*https://repo.magento.com/archives/magento/module-customer-segment/magento-module-customer-segment-102.0.5.0-patch2.zip&quot; (HTTP/1.1 404 - Non trovato)*&quot;.

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud 2.2.x, 2.3.x e 2.4.x

## Problema

Messaggio di errore nella distribuzione che indica che non è stato possibile accedere all’URL dell’archivio.

<u>Passaggi da riprodurre</u>

Attiva la distribuzione manualmente o eseguendo un’unione, un push o una sincronizzazione dell’ambiente.

<u>Risultato effettivo</u>

L’implementazione si blocca. Nel registro degli errori di distribuzione nell’interfaccia utente di Project viene visualizzato un messaggio di errore simile al seguente:

*&quot;Impossibile accedere all&#39;URL &#39;https://repo.magento.com/archives/magento/magento-cloud-configuration/magento-magento-cloud-configuration-x.x.x.x.zip&#39;: HTTP/1.1 \[403 Non consentito o 404 Non trovato\]&quot;*.

Fai clic sull’icona &quot;Errore&quot; nell’interfaccia utente di Project per visualizzare il registro.

<u>Risultato previsto</u>

Distribuzione completata correttamente.

## Causa

L&#39;errore è causato da chiavi di autorizzazione (chiavi di accesso) non valide, non specificate o non specificate correttamente.

Alcuni motivi per cui le chiavi non sono valide sono:

* Hai generato le chiavi utilizzando l’account condiviso.
* La licenza è stata precedentemente revocata per problemi di pagamento.

>[!NOTE]
>
>Se riscontri che è dovuto a un problema di fatturazione o a un contratto scaduto, contatta il team dell’account Adobe per ricevere assistenza e risolvere il problema. Dopo la riattivazione della licenza, verranno ripristinati i diritti relativi a supporto e distribuzione.

## Soluzione

Per risolvere il problema relativo alle chiavi di autorizzazione, attieniti alla seguente procedura (per ulteriori informazioni su ciascuna fase, consulta le sezioni seguenti):

1. Ottieni le chiavi di autorizzazione valide (ignorale se sei assolutamente sicuro che la tua chiave sia valida).
1. Aggiungere il valore delle chiavi nella variabile `env:COMPOSER_AUTH` (o verificare che sia presente il valore corretto) e verificare che le chiavi siano specificate in modo coerente nella variabile a livello di progetto e di ambiente, nonché nel file `auth.json` (se esiste) nella directory principale del progetto.
1. Aggiornare o eliminare `auth.json` in modo che la chiave venga configurata in un&#39;unica posizione, se i valori delle chiavi di autorizzazione non sono specificati o hanno un altro valore.

### 1. Ottenere chiavi di autorizzazione valide

Se utilizzi le chiavi create con l’account condiviso, devi contattare il proprietario della licenza di Adobe Commerce, che ti fornirà l’accesso e richiedere la generazione delle chiavi.

Se la licenza è stata revocata in precedenza a causa di problemi di pagamento e tali problemi sono stati risolti e la licenza è stata rinnovata, è necessario [generare le nuove chiavi di autenticazione](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html?lang=it).

### 2. Aggiungi il valore delle chiavi nella variabile env:COMPOSER\_AUTH e controlla se le stesse chiavi sono specificate in auth.json

Consulta le istruzioni e le informazioni correlate in [Prepara il sistema esistente](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/project/overview) e [Aggiungi chiavi di autenticazione](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/project/overview) nella documentazione per gli sviluppatori.

### 3. Aggiornare o eliminare auth.json

Di seguito è riportata una descrizione dettagliata di come aggiornare le chiavi di autorizzazione:

1. Accedi al computer in cui è installato Adobe Commerce sulle chiavi SSH dell’infrastruttura cloud.
1. Accedi al progetto: `magento-cloud login`
1. Creare un ramo per aggiornare il codice (nell&#39;esempio seguente il nome del ramo è `auth` viene creato dal ramo principale):     `magento-cloud environment:branch auth master`
1. Passa alla directory principale del progetto.
1. Facoltativo: eliminare `auth.json` se si preferisce e continuare con il [passaggio 9](#step9).
1. Apri `auth.json` in un editor di testo.

   ```json
              {
                "http-basic":  {
                    "repo.magento.com": {
                        "username": "<public_key>",
                        "password": "<private_key>"
                        }
                      }
                    }
   ```

1. Aggiungi le chiavi di autenticazione corrette.
1. Salva le modifiche e esci dall’editor di testo.
1. Eseguire il commit e unire le modifiche:

   `git add -A`

   `git commit -m "<message>"`

   `git push origin master`
1. Attendi la distribuzione del progetto.
