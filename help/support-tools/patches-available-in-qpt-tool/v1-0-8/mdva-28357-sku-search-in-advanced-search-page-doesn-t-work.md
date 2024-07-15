---
title: La ricerca SKU MDVA-28357 nella pagina Ricerca avanzata non funziona
description: MDVA-28357 risolve il problema per cui la ricerca eseguita da un SKU di prodotto nella pagina Ricerca avanzata non determina la visualizzazione del prodotto nei risultati della ricerca. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.8. Il problema è stato risolto nella versione 2.4.1 di Adobe Commerce.
exl-id: a89409b0-3155-4fac-9842-0d129dacd6e1
feature: Search
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# La ricerca SKU MDVA-28357 nella pagina Ricerca avanzata non funziona

MDVA-28357 risolve il problema per cui la ricerca eseguita da un SKU di prodotto nella pagina Ricerca avanzata non determina la visualizzazione del prodotto nei risultati della ricerca. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.8. Il problema è stato risolto nella versione 2.4.1 di Adobe Commerce.

## Prodotti e versioni interessati

* Questa patch è stata progettata per Adobe Commerce on-premise 2.3.4-p2.
* La patch è compatibile anche con Adobe Commerce on-premise e Adobe Commerce on cloud infrastructure da 2.3.0 a 2.3.5-p2 e da 2.4.0 a 2.4.0-p1.

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Nella ricerca avanzata, la ricerca tramite uno SKU esegue una query nel campo SKU utilizzando un carattere jolly. Tuttavia, un carattere jolly può essere utilizzato solo con `sku.keyword`, pertanto non restituisce il prodotto previsto.

<u>Passaggi da riprodurre</u>

1. Vai alla pagina Ricerca avanzata.
1. Effettua la ricerca in base a un numero SKU.

<u>Risultato effettivo</u>

Viene visualizzato un messaggio di errore: *Impossibile trovare elementi corrispondenti ai criteri di ricerca. Modifica la ricerca*.

<u>Risultato previsto</u>

Un elemento prodotto viene visualizzato con un messaggio: *1 elemento trovato utilizzando i seguenti criteri di ricerca* *SKU: XX-XXXX*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Applicare le patch utilizzando lo strumento Quality Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento Quality Patches: è stato introdotto un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Per informazioni sulle altre patch disponibili nello strumento QPT, fare riferimento alla sezione [Patch disponibili nello strumento QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
