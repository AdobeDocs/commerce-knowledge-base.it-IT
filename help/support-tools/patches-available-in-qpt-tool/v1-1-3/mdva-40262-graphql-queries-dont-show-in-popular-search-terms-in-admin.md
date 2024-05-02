---
title: "MDVA-40262: le query GraphQL non vengono visualizzate in termini di ricerca comuni in admin"
description: La patch di qualità di MDVA-40262 Adobe Commerce risolve il problema per cui le query di ricerca di GraphQL non vengono visualizzate nei termini di ricerca più comuni nell’amministratore. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.3. L'ID della patch è MDVA-40262. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
exl-id: 7157e47d-a042-4462-96ed-23203a3213bd
feature: Admin Workspace, GraphQL, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# MDVA-40262: le query GraphQL non vengono visualizzate in termini di ricerca comuni in admin

La patch di qualità di MDVA-40262 Adobe Commerce risolve il problema per cui le query di ricerca di GraphQL non vengono visualizzate nei termini di ricerca più comuni nell’amministratore. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.3. L&#39;ID della patch è MDVA-40262. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le query GraphQL non vengono visualizzate nei termini di ricerca più comuni nell’amministratore.

<u>Prerequisiti</u>:

È necessario installare i dati di esempio.

<u>Passaggi da riprodurre</u>:

1. Vai a **Negozi** > **Configurazione** > **Catalogo** > **SEO** > **Termini di ricerca popolari** e impostato su enable.
1. Esegui la seguente query GraphQL:

<pre>
<code class="language-graphql">
{
  products(
    search: "jackets"
    filter: { price: { to: "50" } }
    pageSize: 20
   ) {
    total_count
    items {
      name
      sku
    }
    page_info {
      page_size
      current_page
    }
  }
}
</code>
</pre>

<u>Risultati previsti</u>:

Dopo aver eseguito la query di GraphQL per cercare un prodotto, è necessario aggiungerla ai termini di ricerca più comuni.

<u>Risultati effettivi</u>:

La query di ricerca non viene aggiunta ai termini di ricerca più comuni.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti a seconda del tipo di distribuzione:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sulle patch di qualità per Adobe Commerce, consulta:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sezione.
