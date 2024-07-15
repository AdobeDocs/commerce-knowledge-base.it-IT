---
title: "ACSD-56193: [!DNL Fastly] la cache non è stata cancellata per l'aggiornamento dell'area di gestione temporanea del contenuto"
description: Applica la patch ACSD-56193 per risolvere il problema di Adobe Commerce per cui la cache  [!DNL Fastly]  non viene cancellata per l'aggiornamento dell'area di gestione temporanea del contenuto.
feature: Cache, GraphQL, Staging
role: Admin, Developer
exl-id: d4bbfafa-2d24-44cf-a08b-f7dd9111a65b
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-56193: impossibile cancellare la cache [!DNL Fastly] per l&#39;aggiornamento dell&#39;area di gestione temporanea del contenuto

La patch ACSD-56193 risolve il problema che impedisce la cancellazione della cache [!DNL Fastly] per l&#39;aggiornamento dell&#39;area di gestione temporanea del contenuto. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44. L’ID della patch è ACSD-56193. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Cache [!DNL Fastly/Varnish] non cancellata per l&#39;aggiornamento dell&#39;area di gestione temporanea del contenuto

<u>Passaggi da riprodurre</u>:

1. Installare e configurare la cache [!DNL Varnish].
1. Crea un blocco statico con un aggiornamento pianificato.
1. Crea una categoria che incorpora il blocco statico.
1. Recupera il contenuto della categoria utilizzando la seguente query GraphQL:

   ```GraphQL
      query GetCategories($id: String!) {
         categoryList(filters: { category_uid: { eq: $id } }) 
       {
           meta_title
           meta_keywords
           meta_description
           description
           path
           cms_block {
             content
             identifier
             title
             __typename
           }
           __typename
       }
     }
     {"id":"Mwo="}
   ```

1. Eseguire questa query più volte e assicurarsi che la risposta sia memorizzata nella cache in [!DNL Varnish].
1. Esegui la cron per applicare la modifica pianificata.
1. Esegui nuovamente la query GraphQL precedente.
1. Crea una nuova pianificazione per lo stesso blocco statico.
1. Ripetete i passi da 5 a 9.

<u>Risultati previsti</u>:

Il contenuto aggiornato viene restituito dopo l’esecuzione degli aggiornamenti pianificati.

<u>Risultati effettivi</u>:

Il contenuto obsoleto viene restituito dopo l’esecuzione degli aggiornamenti pianificati.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
