---
title: "ACSD-51700: errore nel cambiare le visualizzazioni dell’archivio nella pagina di modifica del prodotto scaricabile"
description: Applica la patch ACSD-51700 per risolvere il problema di Adobe Commerce in cui si verifica un errore quando si passa da una visualizzazione store a una pagina di modifica del prodotto scaricabile nell’amministratore.
feature: Products
role: Admin
exl-id: 652876a5-275d-437f-9cb3-baf4e7b23aae
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-51700: errore nel cambiare le visualizzazioni dello store nella pagina di modifica del prodotto scaricabile

La patch ACSD-51700 risolve il problema relativo a un errore che si verifica quando si passa da una visualizzazione store a una pagina di modifica del prodotto scaricabile dall’amministratore. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.33. L’ID della patch è ACSD-51700. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6-p1

## Problema

Si verifica un errore quando si passa da una visualizzazione store a una pagina di modifica del prodotto scaricabile nell’amministratore.

<u>Passaggi da riprodurre</u>:

1. Creare un prodotto scaricabile con un nome, [!DNL SKU], e prezzo. Non aggiungere collegamenti e salva il prodotto.
1. Passa da tutte le visualizzazioni dello store alla visualizzazione predefinita dello store.
1. Crea un collegamento per il prodotto scaricabile e salvalo.
1. Passa dalla visualizzazione predefinita dello store a tutte le visualizzazioni dello store.

<u>Risultati previsti</u>:

I prodotti collegati sono visibili.

<u>Risultati effettivi</u>:

Viene visualizzato il seguente errore:

*Funzionalità obsoleta: number_format(): il passaggio di null al parametro #1 ($num) di tipo float è stato dichiarato obsoleto in vendor/magento/module-downloadable/Ui/DataProvider/Product/Form/Modifier/Data/Links.php alla riga 228*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
