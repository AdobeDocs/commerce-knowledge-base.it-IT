---
title: "Patch di Magento MDVA-23764: errore durante il caricamento dei blocchi dinamici"
description: La patch del Magento MDVA-23764 corregge il bug in
exl-id: b884ade6-f88d-4c79-8e84-5a59252abb75
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# Patch di Magento MDVA-23764: errore durante il caricamento dei blocchi dinamici

La patch del Magento MDVA-23764 corregge il bug in

```php
JsFooterPlugin.php
```

che influisce sulla visualizzazione dei blocchi dinamici. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13. Il problema è stato risolto nel Magento 2.3.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione del Magento:** Magento Commerce Cloud 2.3.3.

**Compatibile con le versioni di Magento:** Magento Commerce e Magento Commerce Cloud 2.3.2 - 2.3.4-p2.

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Passaggi da riprodurre:</u>

Prova a caricare un URL simile al seguente: https://\[dominio magento\]/banner/ajax/load/.

<u>Risultato effettivo:</u>

Viene generato un errore simile al seguente: *TypeError non rilevato: strpos() prevede che il parametro 1 sia una stringa, null specificato in...(riga di codice)* .

<u>Risultato previsto:</u>

L’URL viene caricato senza errori.

## Applicare la patch

Per istruzioni su come applicare una patch QPT, utilizzare i seguenti collegamenti in base al prodotto di Magento:

* Magento Commerce: DevDocs [Applica patch tramite lo strumento Patch di qualità](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* Magento Commerce Cloud: DevDocs [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) .

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: è stato creato un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Verificare se la patch è disponibile per il problema del Magento utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Per informazioni sulle altre patch disponibili nello strumento QPT, fare riferimento alla sezione [Patch disponibili nello strumento QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
