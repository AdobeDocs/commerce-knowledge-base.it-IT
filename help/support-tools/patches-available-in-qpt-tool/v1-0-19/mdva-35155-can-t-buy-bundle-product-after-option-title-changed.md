---
title: "MDVA-35155: impossibile acquistare il prodotto bundle dopo la modifica del titolo dell'opzione"
description: La patch MDVA-35155 risolve il problema che impedisce l'acquisto di un prodotto bundle dopo la modifica del titolo dell'opzione. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19. L'ID della patch è MDVA-35155. Il problema è stato risolto nella versione 2.4.3 di Adobe Commerce.
exl-id: 79770c69-1bb0-48d8-acdf-c8c1272f9da8
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# MDVA-35155: impossibile acquistare il prodotto bundle dopo la modifica del titolo dell&#39;opzione

La patch MDVA-35155 risolve il problema che impedisce l&#39;acquisto di un prodotto bundle dopo la modifica del titolo dell&#39;opzione. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19. L&#39;ID della patch è MDVA-35155. Il problema è stato risolto nella versione 2.4.3 di Adobe Commerce.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.5

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce on-premise e Adobe Commerce sull’infrastruttura cloud 2.3.0-2.3.5-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I prodotti bundle non possono essere acquistati dopo la modifica del titolo dell’opzione.

<u>Passaggi da riprodurre</u>:

1. Crea un nuovo prodotto bundle tramite **Importazione prodotto**.
1. Il prodotto è normale sia nell’Admin che nel front-end (disponibile e può essere aggiunto al carrello).
1. Aggiornare lo stesso prodotto con le modifiche apportate al nome in `bundle_values` e reimportare il prodotto.

<u>Risultati previsti</u>:

L’opzione del bundle esistente viene aggiornata al nuovo nome e contiene gli stessi elementi.

<u>Risultati effettivi</u>:

* L’amministratore tenta di unire i prodotti con lo stesso SKU in una singola sezione di opzione bundle, che si traduce in una sezione di opzione vuota.
* Il prodotto è esaurito sul front-end (anche dopo una reindicizzazione).

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
