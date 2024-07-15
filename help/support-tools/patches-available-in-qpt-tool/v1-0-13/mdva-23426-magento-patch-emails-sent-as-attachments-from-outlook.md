---
title: "Patch di Magento MDVA-23426: e-mail inviate come allegati da Outlook"
description: La patch del Magento MDVA-23426 risolve il problema relativo all'invio di e-mail come allegati da parte del Magento da MS Outlook. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13. Il problema è stato risolto nel Magento 2.3.5.
exl-id: 0b4c3e33-76c5-48b0-b1a8-a967cea11b98
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# Patch di Magento MDVA-23426: e-mail inviate come allegati da Outlook

La patch del Magento MDVA-23426 risolve il problema relativo all&#39;invio di e-mail come allegati da parte del Magento da MS Outlook. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13. Il problema è stato risolto nel Magento 2.3.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione del Magento:** Magento Commerce Cloud 2.3.3.

**Compatibile con le versioni di Magento:** Magento Commerce e Magento Commerce Cloud 2.3.3 - 2.3.4-p2.

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le e-mail vengono ricevute con un corpo vuoto e il contenuto viene incluso come allegato.

<u>Prerequisiti:</u> Outlook/Exchange è utilizzato come combinazione client/server.

<u>Passaggi da riprodurre:</u> 1. Sottomettere un ordine, la notifica dell&#39;ordine o la notifica di spedizione viene inviata.2. L’e-mail viene ricevuta.

<u>Risultato effettivo:</u> l&#39;e-mail viene visualizzata con un corpo vuoto e il contenuto incluso come allegato ATT\* all&#39;e-mail. <u>Risultato previsto:</u>

L’e-mail viene ricevuta senza allegati e il corpo dell’e-mail contiene il contenuto.

## Applicare la patch

Per istruzioni su come applicare una patch QPT, utilizzare i seguenti collegamenti in base al prodotto di Magento:

* Magento Commerce: DevDocs [Applica patch tramite lo strumento Patch di qualità](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* Magento Commerce Cloud: DevDocs [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) .

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: è stato creato un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Verificare la presenza di problemi di Magento nella patch con lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Per informazioni sulle altre patch disponibili nello strumento QPT, fare riferimento alla sezione [Patch disponibili nello strumento QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
