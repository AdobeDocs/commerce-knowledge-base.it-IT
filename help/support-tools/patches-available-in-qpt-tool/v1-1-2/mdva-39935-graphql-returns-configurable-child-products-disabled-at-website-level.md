---
title: "MDVA-39935: GraphQL restituisce prodotti secondari configurabili disabilitati a livello di sito Web"
description: La patch di MDVA-39935 Adobe Commerce risolve il problema relativo alla restituzione da parte di GraphQL di prodotti secondari configurabili disattivati a livello di sito Web. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.2. L'ID della patch è MDVA-39935. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
exl-id: 45bd6bd9-3572-4477-a689-d6b952a3290a
feature: GraphQL, Configuration, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# MDVA-39935: GraphQL restituisce prodotti secondari configurabili disabilitati a livello di sito Web

La patch di MDVA-39935 Adobe Commerce risolve il problema relativo alla restituzione da parte di GraphQL di prodotti secondari configurabili disattivati a livello di sito Web. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.2. L&#39;ID della patch è MDVA-39935. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.1 - 2.4.3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

GraphQL restituisce prodotti secondari configurabili anche dopo che sono stati disabilitati a livello di sito Web.

<u>Passaggi da riprodurre</u>:

1. Abilita l&#39;opzione di visualizzazione prodotti esauriti in **Archivia** > **Configurazione** > **Catalogo** > **Inventario** > **Opzioni Stock** > **Visualizza prodotti esauriti** > **Sì**.
1. Seleziona qualsiasi **Prodotto configurabile** che ha più di due **Prodotti semplici**.
1. Disattiva **Prodotto semplice** e salva **Prodotto configurabile**.
1. Recupera il **Prodotto configurabile** dati tramite GraphQL.

<pre>
  <code class="language-graphql">
{
  products(filter: { sku: { eq: "cp1" } }) {
    items {
      __typename
      name
      sku
      ... on ConfigurableProduct {
        variants {
          product {
            __typename
            name
            sku
            color
            stock_status
          }
        }
      }
    }
  }
}
</code>
</pre>

<u>Risultati previsti</u>:

I prodotti disattivati NON vengono visualizzati nei risultati delle varianti.

<u>Risultati effettivi</u>:

I dati dei prodotti disattivati vengono recuperati nei risultati delle varianti.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti a seconda del tipo di distribuzione:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sulle patch di qualità per Adobe Commerce, consulta:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sezione.
