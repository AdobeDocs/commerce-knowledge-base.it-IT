---
title: 'MDVA-38447: i prodotti secondari configurabili "Not visible individual" vengono restituiti nella risposta di GraphQL e la query MySQL è lenta'
description: La patch di MDVA-38447 Adobe Commerce risolve il problema relativo alla restituzione di prodotti secondari configurabili "Non visibile singolarmente" nella risposta di GraphQL e alla lentezza della query MySQL per i prodotti GraphQL con filtro categoria. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2. L'ID della patch è MDVA-38447. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
exl-id: 302e7458-d9ea-466a-a2ac-d86a8ee3eca3
feature: B2B, GraphQL, Categories, Configuration, Products, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# MDVA-38447: i prodotti secondari configurabili &quot;Not visible individual&quot; vengono restituiti nella risposta di GraphQL e la query MySQL è lenta

La patch di MDVA-38447 Adobe Commerce risolve il problema relativo alla restituzione di prodotti secondari configurabili &quot;Non visibile singolarmente&quot; nella risposta di GraphQL e alla lentezza della query MySQL per i prodotti GraphQL con filtro categoria. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2. L&#39;ID della patch è MDVA-38447. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Nella risposta di GraphQL vengono restituiti prodotti secondari configurabili &quot;Non visibili singolarmente&quot; e la query MySQL lenta per la query prodotti GraphQL con filtro categoria.

<u>Prerequisiti</u>:

I moduli B2B devono essere installati.

<u>Passaggi da riprodurre</u>:

1. Creare un prodotto configurabile con prodotti semplici impostati su **Non visibile singolarmente**.
1. Esegui una **reindicizzazione completa**.
1. Esegui una **Query GraphQL** mi piace:

<pre>query getFilteredProducts( $filter: ProductAttributeFilterInput!
  $sort: ProductAttributeSortInput.
  $search: String $pageSize: Int!
  $currentPage: Int!
) { products( filtro: $filter ordinamento: $sort ricerca: $search pageSize: $pageSize currentPage: $currentPage ) { total_count page_info { total_pages_size_page_size } elementi { name sku } } }</pre>

Variabili:

<pre>{"filter":{"user_group":{"eq":""}},"search":"config-100","sort":{},"pageSize":200,"currentPage":1}
</pre>

<u>Risultati previsti</u>:

I prodotti con visibilità impostata su &quot;Non visibile singolarmente&quot; non verranno restituiti nella risposta.

<u>Risultati effettivi</u>:

I prodotti con visibilità impostata su &quot;Non visibile singolarmente&quot; vengono restituiti in risposta.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti a seconda del tipo di distribuzione:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sulle patch di qualità per Adobe Commerce, consulta:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sezione.
