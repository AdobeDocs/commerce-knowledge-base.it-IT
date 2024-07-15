---
title: "MDVA-37913: i collegamenti per il download del prodotto scompaiono dopo l’aggiornamento degli attributi di estensione tramite API"
description: La patch MDVA-37913 per risolve il problema della scomparsa dei collegamenti di prodotto scaricabili dopo l'aggiornamento degli attributi dell'estensione tramite API. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24. L'ID della patch è MDVA-37913. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.3.
exl-id: e4b2cf59-5c35-4a28-a63e-15cd7d0d5a5d
feature: REST, Attributes, Extensions, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# MDVA-37913: i collegamenti per il download del prodotto scompaiono dopo l’aggiornamento degli attributi dell’estensione tramite API

La patch MDVA-37913 per risolve il problema della scomparsa dei collegamenti di prodotto scaricabili dopo l&#39;aggiornamento degli attributi dell&#39;estensione tramite API. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24. L&#39;ID della patch è MDVA-37913. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.3.


## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**
Adobe Commerce sull’infrastruttura cloud 2.3.6

**Compatibile con le versioni di Adobe Commerce:**
Adobe Commerce on-premise e Adobe Commerce sull’infrastruttura cloud 2.3.0 - 2.4.0-p1
>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.


## Problema

I collegamenti dei prodotti scaricabili scompaiono dopo l’aggiornamento degli attributi dell’estensione tramite API.

<u>Prerequisiti</u>:
Prodotto scaricabile con collegamenti per il download.

<u>Passaggi da riprodurre</u>:

1. Aggiorna gli attributi dell&#39;estensione utilizzando una richiesta come questa:

```JSON
{
    "product": {
        "extension_attributes": {
            "stock_item": {
                "is_in_stock": true,
                "qty": 100
            }
        }
    }
}
```

<u>Risultati previsti</u>:<br>
Il prodotto è stato aggiornato, tutti i collegamenti di download non vengono rimossi.

<u>Risultati effettivi</u>:<br>
Prodotto aggiornato, ma tutti i collegamenti di download sono stati rimossi.


## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html)

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità nella nostra knowledge base di supporto, consulta:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

Per informazioni sulle altre patch disponibili nello strumento QPT, consulta la sezione [Patch disponibili nello strumento QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) nella nostra knowledge base di supporto.
