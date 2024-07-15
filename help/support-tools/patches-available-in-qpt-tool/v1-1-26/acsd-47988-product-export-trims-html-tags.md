---
title: "ACSD-47988: esportazione del prodotto taglia i tag HTML dalla descrizione del prodotto di page builder"
description: Applica la patch ACSD-47988 per risolvere il problema di Adobe Commerce, in cui l’esportazione del prodotto taglia i tag HTML dalla descrizione del prodotto del generatore di pagine.
exl-id: 96c45ca8-f526-4876-8f2c-39bce07f86eb
feature: Admin Workspace, Data Import/Export, Page Builder, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-47988: esportazione del prodotto taglia i tag HTML dalla descrizione del prodotto di page builder

La patch ACSD-47988 risolve il problema relativo all’esportazione dei prodotti che taglia i tag HTML dalla descrizione del prodotto Page Builder. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26. L’ID della patch è ACSD-47988. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’esportazione del prodotto taglia i tag HTML dalla descrizione del prodotto di Page Builder.

<u>Passaggi da riprodurre</u>:

1. Crea prodotti con alcuni HTML nella descrizione. Utilizza l’elemento HTML del generatore di pagine per inserire HTML.
1. Esporta i prodotti utilizzando la funzionalità di importazione/esportazione di Adobe Commerce.
1. Importa il file CSV esportato.
1. Apri il prodotto e controlla gli elementi HTML nella descrizione.

<u>Risultati previsti</u>:

I tag HTML rimangono nella descrizione del prodotto dopo l’importazione dello stesso contenuto.

<u>Risultati effettivi</u>:

I tag HTML vengono rimossi dopo l’importazione.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
