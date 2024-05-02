---
title: "MDVA-22026: impossibile importare le immagini di prodotto dall'URL esterno"
description: La patch MDVA-22026 risolve il problema dell'impossibilità di importare immagini di prodotto da un URL esterno.
exl-id: 29043c6c-daf2-4925-85bf-49eeeee3742c
feature: Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# MDVA-22026: impossibile importare le immagini di prodotto dall&#39;URL esterno

La patch MDVA-22026 risolve il problema dell&#39;impossibilità di importare immagini di prodotto da un URL esterno.

Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20. L&#39;ID della patch è MDVA-22026. Il problema è stato risolto nella versione 2.3.4 di Adobe Commerce.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:** Adobe Commerce sull’infrastruttura cloud 2.3.2-p2

**Compatibile con le versioni di Adobe Commerce:** Adobe Commerce on-premise e Adobe Commerce sull’infrastruttura cloud 2.3.2-2.3.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Passaggi da riprodurre</u>:

1. In Amministratore, vai a **Sistema** > **Importa**.
1. Imposta **Tipo di entità** = *Prodotti*.
1. Imposta **Comportamento di importazione** = *Aggiungi/aggiorna*.
1. Imposta **Conteggio errori consentiti** = *10000*.
1. Selezionare il file da importare.
1. Fai clic su **Verifica dati** (che deve convalidare il file).
1. Fai clic su **Importa** pulsante.

<u>Risultati previsti</u>:

Importazione corretta dei prodotti dai file CSV, incluse le immagini dagli URL esterni, come previsto.

<u>Risultati effettivi</u>:

Importazione non riuscita di prodotti da file CSV, incluse immagini da URL esterni, e ricevi un errore simile:

```php
1. Imported resource (image) could not be downloaded from external resource due to timeout or access permissions in row(s): 4, 5, 8, 9, 16, 18, 20, 21, 22, 23, 26, 27, 28, 52, 53, 55, 58, 63, 70, 71, 77, 78, 83, 84, 91
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti riportati di seguito, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html).
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html).

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Verifica la patch per il problema Adobe Commerce con lo strumento Quality Patches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Per informazioni sulle altre patch disponibili nello strumento QPT, consultare [Patch disponibili nello strumento QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sezione.
