---
title: "MDVA-37225: l'ordine rapido non funziona con SKU integer"
description: La patch di qualità MDVA-37225 per Adobe Commerce risolve il problema quando la pagina non viene caricata durante la creazione di un ordine rapido quando è presente un valore intero negli SKU importati. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23. L'ID della patch è MDVA-37225. Il problema è pianificato per la risoluzione in Adobe Commerce versione 2.4.3.
exl-id: ecd2b9d7-ca68-4372-b0c5-55e2a3301586
feature: B2B, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# MDVA-37225: l&#39;ordine rapido non funziona con SKU integer

La patch di qualità MDVA-37225 per Adobe Commerce risolve il problema quando la pagina non viene caricata durante la creazione di un ordine rapido quando è presente un valore intero negli SKU importati. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23. L&#39;ID della patch è MDVA-37225. Il problema è pianificato per la risoluzione in Adobe Commerce versione 2.4.3.

## Prodotti e versioni interessati

* La patch è stata progettata per Adobe Commerce sull’infrastruttura cloud 2.4.1-p1
* La patch è compatibile anche con Adobe Commerce on-premise e Adobe Commerce on cloud infrastructure 2.4.1-2.4.2-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Prerequisito</u>:

Adobe Commerce con modulo B2B installato

<u>Passaggi da riprodurre</u>:

1. Abilita la funzionalità di ordine rapido B2B.
1. Crea 4 prodotti semplici con SKU (ad esempio SKU: *00100*, *001E002*, *001E02C* e *7100824*).
1. Vai alla pagina ``<storefront_url>/quickorder`` sul front-end e prova a creare un ordine utilizzando un file CSV con questo contenuto di esempio:

| sku | qtà |
|---|---|
| 00100 | 1 |


<u>Risultati previsti</u>:

Il prodotto (esempio: prodotto con SKU = *00100*) viene aggiunto al carrello, come previsto.

<u>Risultati effettivi</u>:

La pagina non viene caricata e nessun prodotto viene aggiunto al carrello.


## Applicare la patch

Per applicare singole patch, utilizza i seguenti collegamenti nella documentazione per gli sviluppatori, a seconda del prodotto Adobe Commerce:

* Adobe Commerce e Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html)

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità nella nostra knowledge base di supporto, consulta:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

Per informazioni sulle altre patch disponibili nello strumento QPT, consulta la sezione [Patch disponibili nello strumento QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) nella nostra knowledge base di supporto.
