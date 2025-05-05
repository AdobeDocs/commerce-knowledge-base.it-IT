---
title: 'ACSD-47332: errore cron segnalato solo tra 00:00 e 00:59 UTC'
description: Applica la patch ACSD-47332 per risolvere il problema Adobe Commerce in cui cron non riesce e viene segnalato un errore solo quando è in esecuzione tra le 00:00 e le 00:59 UTC.
exl-id: a4eac977-6d0a-4e36-8576-68777c1e40b2
feature: Configuration
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# ACSD-47332: errore cron segnalato solo quando si esegue tra le 00:00 e le 00:59 UTC

La patch ACSD-47332 risolve il problema relativo all’errore cron, che viene segnalato solo quando il cron è in esecuzione tra le 00:00 e le 00:59 UTC. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.22. L’ID della patch è ACSD-47332. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il Cron ha esito negativo con un errore segnalato solo quando si esegue tra le 00:00 e le 00:59 UTC.

<u>Passaggi da riprodurre</u>:

1. Eseguire il CRON `catalog_index_refresh_price` tra le 00:00 e le 00:59 UTC.

<u>Risultati previsti</u>:

Cron non mostra errori.

<u>Risultati effettivi</u>:

Cron non riesce e viene visualizzato il seguente errore.

```SQL
SQLSTATE[HY093]: Invalid parameter number: number of bound variables does not match number of tokens, query was: SELECT `cat`.`entity_id` FROM `c
  atalog_product_entity_datetime` AS `attr`
   LEFT JOIN `catalog_product_entity` AS `cat` ON cat.row_id= attr.row_id AND (cat.created_in <= 1 AND cat.updated_in > 1) WHERE (attr.attribute_id
   = '79') AND (attr.store_id = '0') AND (attr.value = DATE_FORMAT('2022-10-02', '%Y-%m-%d %H:%i:%s'))
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
