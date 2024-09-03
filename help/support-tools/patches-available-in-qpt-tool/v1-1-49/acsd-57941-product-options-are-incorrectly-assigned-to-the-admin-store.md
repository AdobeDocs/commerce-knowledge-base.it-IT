---
title: "ACSD-57941: le opzioni del prodotto non sono assegnate correttamente all’archivio di amministrazione"
description: Applica la patch ACSD-57941 per risolvere il problema di Adobe Commerce, a causa del quale le opzioni di prodotto non vengono assegnate correttamente all’archivio di amministrazione anziché ai rispettivi archivi.
feature: Products
role: Admin, Developer
source-git-commit: 1cc673716b75bda6cfe7b3d597ec94e4510fa7e4
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---


# ACSD-57941: le opzioni di prodotto non sono assegnate correttamente all’archivio di amministrazione

La patch ACSD-57941 risolve il problema relativo all’assegnazione errata delle opzioni prodotto all’archivio di amministrazione anziché ai rispettivi archivi. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49. L’ID della patch è ACSD-57941. Il problema è stato risolto in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le opzioni prodotto non vengono assegnate correttamente all’archivio di amministrazione anziché ai rispettivi archivi.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto semplice.
1. Importa lo stesso prodotto con alcune opzioni personalizzate.
1. Vai a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** e apri il prodotto creato. Fare clic su **[!UICONTROL Customizable options]** e assicurarsi che le opzioni importate siano visibili.
1. Importa lo stesso file altre volte.

<u>Risultati previsti</u>:

Le opzioni personalizzate vengono aggiornate.

<u>Risultati effettivi</u>:

Le opzioni personalizzate del prodotto sono duplicate.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
