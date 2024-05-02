---
title: "MDVA-37182: risultati di ricerca incoerenti negli Elasticsearch 6 e 7"
description: La patch MDVA-37182 risolve il problema con un comportamento di ricerca incoerente tra le versioni 6 e 7 di Elasticsearch. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22. L'ID della patch è MDVA-37182. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.3.
exl-id: 6c4e2d2f-cced-487d-b253-fd0c80bc6067
feature: Search, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# MDVA-37182: risultati di ricerca incoerenti negli Elasticsearch 6 e 7

La patch MDVA-37182 risolve il problema con un comportamento di ricerca incoerente tra le versioni 6 e 7 di Elasticsearch. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22. L&#39;ID della patch è MDVA-37182. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:** Adobe Commerce sull’infrastruttura cloud 2.4.1

**Compatibile con le versioni di Adobe Commerce:** Adobe Commerce on-premise e Adobe Commerce sull’infrastruttura cloud 2.4.1-2.4.2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Comportamento di ricerca incoerente.

<u>Passaggi da riprodurre</u>:

1. Crea prodotti con i seguenti dettagli:
   * Nomi: &quot;5127AC&quot;, &quot;5127SS&quot;, &quot;5127AB&quot;
   * SKU: &quot;product1&quot;, &quot;product2&quot;, &quot;product3&quot;
1. Impostare motore di ricerca su Elasticsearch 6 (ES6).
1. Esegui reindicizzazione completa.
1. Nella vetrina, cerca &quot;5127s&quot;.
1. Imposta motore di ricerca sull&#39;Elasticsearch 7 (ES7).
1. Esegui reindicizzazione completa.
1. Nella vetrina, cerca &quot;5127s&quot;.

<u>Risultato effettivo:</u>:

ES6: la ricerca non restituisce alcun risultato.ES7: la ricerca restituisce tre prodotti.

<u>Risultato previsto:</u>:

La ricerca restituisce un prodotto per entrambe le versioni.

## Applicare la patch

Per applicare singole patch, utilizzare i seguenti collegamenti, a seconda del prodotto Adobe Commerce:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili nello strumento QPT, consultare [Patch disponibili nello strumento QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sezione.
