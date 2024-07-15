---
title: "ACSD-51120: impossibile cancellare la cache delle richieste di GET di GraphQL per le pagine CMS che contengono blocchi CMS"
description: Applica la patch ACSD-51120 per risolvere il problema di Adobe Commerce per cui la cache delle richieste di GraphQL GET non viene cancellata per le pagine CMS che contengono blocchi CMS.
exl-id: 22abba89-b697-45d7-972e-bf3233e5e9ec
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-51120: impossibile cancellare la cache delle richieste di GET di GraphQL per le pagine CMS che contengono blocchi CMS

La patch ACSD-51120 risolve il problema per cui la cache delle richieste di GET di GraphQL non viene cancellata per le pagine CMS che contengono blocchi CMS aggiornati tramite un aggiornamento di staging. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33. L’ID della patch è ACSD-51120. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.2-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La cache delle richieste di GraphQL GET non viene cancellata per le pagine CMS che contengono blocchi CMS aggiornati tramite un aggiornamento di staging.

<u>Passaggi da riprodurre</u>:

1. Crea un blocco CMS.
1. Includere il blocco CMS in una pagina CMS utilizzando [!DNL Page Builder].
1. Recupera la pagina CMS utilizzando la query GraphQL specificata utilizzando una richiesta GET:

   ```GraphQL
   {
   cmsPage( identifier: "<CMS PAGE IDENTIFIER>") {
       content
       content_heading
       identifier
       meta_description
       meta_keywords
       meta_title
       page_layout
       title
       url_key
   }
   }
   ```

1. Assicurarsi che la risposta di GraphQL sia memorizzata nella cache in [!DNL Varnish].
1. Crea un aggiornamento pianificato per il blocco.
1. Attendi l’applicazione dell’aggiornamento pianificato ed esegui il processo cron per applicare l’aggiornamento pianificato.
1. Recupera nuovamente la pagina CMS utilizzando la query GraphQL specificata e una richiesta GET.

<u>Risultati previsti</u>:

La risposta mostra il contenuto aggiornato.

<u>Risultati effettivi</u>:

La risposta mostra ancora il contenuto precedente.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.


## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
