---
title: "ACSD-54067: il video del prodotto non viene riprodotto su dispositivo mobile"
description: Applica la patch ACSD-54067 per risolvere il problema di Adobe Commerce, se un video prodotto non viene riprodotto su un dispositivo mobile.
feature: Media, Products
role: Admin, Developer
exl-id: 369650ef-bcce-47c5-bbfe-39f3c2b1d73f
source-git-commit: 0795e3e0ba11002c8aff2794e16fa05f1c7e19c3
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-54067: il video prodotto non viene riprodotto su un dispositivo mobile

La patch ACSD-54067 risolve il problema della mancata riproduzione di un video prodotto su un dispositivo mobile. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.41. L’ID della patch è ACSD-54067. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Un video di prodotto non viene riprodotto su un dispositivo mobile.

<u>Passaggi da riprodurre</u>:

1. Installa Adobe Commerce.
1. Esegui il comando:
   `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`.
1. Vai a **[!UICONTROL Admin product list]** pagina e filtro per *[!UICONTROL SKU product_dynamic_120]*.
1. Apri la pagina del prodotto e vai a **[!UICONTROL Images and Videos]** > aggiungi un video > compila l’URL: https://vimeo.com/347119375 e salva.
1. Vai alla vetrina e apri la pagina del prodotto per *[!UICONTROL product_dynamic_120]*.
1. Imposta il browser su *dispositivo mobile* con una larghezza di *320 px* e aggiorna.
1. Nel cursore della galleria, selezionare il video e fare clic su per riprodurlo.

<u>Risultati previsti</u>:

Viene riprodotto il video del prodotto.

<u>Risultati effettivi</u>:

Il video del prodotto non viene riprodotto.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
