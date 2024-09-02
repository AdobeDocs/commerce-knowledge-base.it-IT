---
title: "ACSD-58739: la reindicizzazione parziale genera un errore"
description: Applica la patch ACSD-55241 per risolvere il problema di Adobe Commerce che genera un errore a causa della reindicizzazione parziale.
feature: Inventory, Products
role: Admin, Developer
source-git-commit: b21eab3bf8ec492f0b1c5be9c13c6c579f43fe44
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# ACSD-58739: la reindicizzazione parziale genera un errore

La patch ACSD-58739 risolve il problema relativo alla reindicizzazione parziale che genera un errore. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49. L’ID della patch è ACSD-58739. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7 - 2.4.8

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La reindicizzazione parziale genera un errore.

<u>Passaggi da riprodurre</u>:

1. Aggiungere le impostazioni di connessione slave a `app/etc/ev.php`.
1. Genera fino a 10000 prodotti ed esegui il comando seguente:

   ```
   bin/magento index:reindex
   ```

1. Aggiungere gli ID prodotto generati nella tabella del database `catalogsearch_fulltext_cl`.

   ```
   insert into catalogsearch_fulltext_cl (entity_id) select entity_id from catalog_product_entity;
   ```

1. Esegui il comando seguente per attivare la reindicizzazione parziale:

   ```
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1 
   ```

1. Controllare il file `var/log/support_report.log`.

<u>Risultati previsti</u>

Nessun errore.

<u>Risultati effettivi</u>:

*Impossibile trovare la tabella o la visualizzazione di base*. Errore durante la reindicizzazione parziale.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
