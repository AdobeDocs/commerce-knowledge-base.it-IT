---
title: "MDVA-30186: opzioni attributo non ordinato nella risposta di GraphQL"
description: La patch MDVA-30186 risolve il problema che non consente di ordinare le opzioni di attributo nella risposta di GraphQL. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23. L'ID della patch è MDVA-30186. Il problema è stato risolto in Adobe Commerce 2.4.3.
exl-id: 7b2aef16-5012-4206-9444-e0b765f0c0c9
feature: Attributes, GraphQL, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-30186: opzioni attributo non ordinato nella risposta di GraphQL

La patch MDVA-30186 risolve il problema che non consente di ordinare le opzioni di attributo nella risposta di GraphQL. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23. L&#39;ID della patch è MDVA-30186. Il problema è stato risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce sull’infrastruttura cloud 2.3.4 e 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.4 - 2.3.5-p2, 2.4.0 - 2.4.0-p1 e 2.4.2 - 2.4.2-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Passaggi da riprodurre</u>:

1. Aggiungi tre opzioni all’attributo di colore esistente.
1. Crea sei prodotti semplici con opzioni (Esempio: *Opzione 1*: 1 prodotto, *Opzione 2*: 2 prodotti, *Opzione 3*: 3 prodotti).
1. Crea una categoria e assegna tutti i prodotti creati in precedenza.
1. Effettua ora la seguente richiesta GraphQL con il tuo ID categoria:

   <pre><code class="language-graphql">
    {
      products(
        filter: { category_id: { eq: "3" } }
        pageSize: 200
        currentPage: 1
        sort: { name: ASC }
      ) {
        aggregations {
          attribute_code
          count
          label
          options {
            count
            label
            value
          }
        }
        items {
          name
          sku
          url_key
        }
      }
    }
    </code></pre>

1. Ora modifica l’ordinamento delle opzioni attributo dalla pagina di modifica degli attributi in Admin.
1. Ripeti la richiesta GraphQL precedente e osserva le opzioni dell’attributo colore.

<u>Risultati previsti</u>:

Le opzioni dell’attributo sono ordinate in base all’ordine impostato dall’amministratore.

<u>Risultati effettivi</u>:

Le opzioni dell’attributo sono sempre ordinate in base al numero di prodotti associati.


## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
