---
title: 'ACSD-53728: il completamento dell''indicizzatore EAV del prodotto richiede molto tempo'
description: Applicare la patch ACSD-53728 per risolvere il problema Adobe Commerce, in cui il completamento dell'indicizzatore EAV del prodotto richiede molto tempo.
feature: Products, Attributes
role: Admin, Developer
exl-id: 3e0601fb-7e2c-4f1b-8bd9-d2f09092db0e
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# ACSD-53728: il completamento dell&#39;indicizzatore EAV del prodotto richiede molto tempo

La patch ACSD-53728 risolve il problema relativo al tempo di completamento dell&#39;indicizzatore EAV del prodotto. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.37. L’ID della patch è ACSD-53728. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il completamento dell’indicizzatore EAV del prodotto richiede molto tempo.

<u>Passaggi da riprodurre</u>:

1. Crea un numero elevato di prodotti (ad esempio, circa 1300 prodotti configurabili).
1. Esegui la reindicizzazione EAV del prodotto e misura il tempo:

   `run bin/magento index:reindex catalog_product_attribute`

<u>Risultati previsti</u>:

La reindicizzazione richiede un tempo ragionevole.

<u>Risultati effettivi</u>:

La reindicizzazione richiede molto tempo.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
