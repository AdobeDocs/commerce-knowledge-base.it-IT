---
title: "MDVA-36170: la query GraphQL nella categoria restituisce dati non memorizzati in cache"
description: La patch MDVA-36170 risolve il problema che impedisce la memorizzazione nella cache del risultato della query GraphQL. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20. L'ID della patch è MDVA-36170. Il problema è stato risolto in Adobe Commerce 2.4.2.
exl-id: 6249b751-4b71-4833-ab86-ded615d648a8
feature: Cache, GraphQL, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# MDVA-36170: la query GraphQL nella categoria restituisce dati non memorizzati nella cache

La patch MDVA-36170 risolve il problema che impedisce la memorizzazione nella cache del risultato della query GraphQL. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20. L&#39;ID della patch è MDVA-36170. Il problema è stato risolto in Adobe Commerce 2.4.2.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.6

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.1 - 2.4.1-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

È stato risolto il problema che impediva la memorizzazione nella cache del risultato della query GraphQL.

<u>Passaggi da riprodurre</u>:

Il commerciante utilizza il metodo GET per il caching di GraphQL, ma non ottiene i dati memorizzati nella cache.

<pre>https://magento_url/graphql?query={ products(filtro: {category_id: {eq: "2"}}, dimensioni pagina: 2000, pagina corrente: 1, ordinamento: {position: ASC}) {
elementi {
  sku
  id
  nome
  descrizione {
    html
  }
  url_key
  specifiche
  immagine {
    etichetta
    gallery_url
  }
  __typename
  quantity_in
  small_image {
    gallery_url
    etichetta
  }
  product_price_range {
    maximum_price {
      final_price {
        valore
      }
    }
    prezzo_minimo {
      final_price {
        valore
      }
    }
  }
  ... su ConfigurableProduct {
    varianti{
      attributi{
        codice
        etichetta
        value_index
      }
      product{
        sku
        quantity_in
      }
    }
   }
  }
}
}}</pre>

<u>Risultati previsti</u>:

I dati vengono memorizzati nella cache.

<u>Risultati effettivi</u>:

I dati non sono memorizzati in cache.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
