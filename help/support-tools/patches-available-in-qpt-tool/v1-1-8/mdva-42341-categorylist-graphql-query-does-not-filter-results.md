---
title: 'MDVA-42341: la query GraphQL "categoryList" non filtra i risultati'
description: La patch MDVA-42341 risolve il problema per cui la query GraphQL "categoryList" non filtra i risultati se una richiesta ha l'intestazione Store. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8. L'ID della patch è MDVA-42341. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
exl-id: 34aeb30a-9491-4102-b33e-dcd857b6a1c2
feature: GraphQL, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-42341: la query GraphQL &quot;categoryList&quot; non filtra i risultati

La patch MDVA-42341 risolve il problema per cui la query GraphQL &quot;categoryList&quot; non filtra i risultati se una richiesta ha l&#39;intestazione Store. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8. L&#39;ID della patch è MDVA-42341. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La query GraphQL &quot;categoryList&quot; non filtra i risultati se una richiesta ha l’intestazione Store.

<u>Passaggi da riprodurre</u>:

1. Crea una nuova Categoria principale e denominala **root2**.
1. Crea un secondo sito Web/store/storeview e assegna **root2** nel nuovo Store.
1. Crea una nuova categoria in Categoria principale predefinita = categoria1.
1. Utilizzando una richiesta di GraphQL, ottieni un elenco di categorie per il secondo sito web (usa Archivio intestazioni = nuovo).

<pre>
<code class="language-graphql">
{
  categoryList(filters: {name: {match: "category1"}}) {
    uid
    level
    name
    breadcrumbs {
      category_uid
      category_name
      category_level
      category_url_key
    }
  }
}
</code>
</pre>

<u>Risultati previsti</u>:

Le categorie della categoria principale predefinita non sono elencate in risposta perché si sta utilizzando una &quot;nuova&quot; intestazione store.

<u>Risultati effettivi</u>:

Le categorie della categoria principale predefinita sono disponibili nei risultati.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
