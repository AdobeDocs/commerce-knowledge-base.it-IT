---
title: "MDVA-40488: prodotti configurabili con prodotti secondari esauriti non visualizzati nell'intervallo di prezzo corretto"
description: La patch MDVA-40488 risolve il problema se i prodotti configurabili con prodotti secondari esauriti non vengono visualizzati nella giusta fascia di prezzo. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9. L'ID della patch è MDVA-40488. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
exl-id: 0c4b9f5e-ae41-409e-b244-1d7cf948ed6f
feature: Configuration, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 0%

---

# MDVA-40488: prodotti configurabili con prodotti secondari esauriti non visualizzati nell&#39;intervallo di prezzo corretto

La patch MDVA-40488 risolve il problema se i prodotti configurabili con prodotti secondari esauriti non vengono visualizzati nella giusta fascia di prezzo. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9. L&#39;ID della patch è MDVA-40488. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I prodotti configurabili con prodotti secondari esauriti non vengono visualizzati nella giusta fascia di prezzo.

<u>Prerequisiti</u>:

Vai a Amministrazione Commerce > **store** > **configurazione** > **catalogo** > **Inventario** > **stock options** e imposta **Visualizza prodotti esauriti** configurazione a *Sì*.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto configurabile con due prodotti associati. Ad esempio: prodotti semplici Rosso e Marrone.
1. Impostare l&#39;inventario del prodotto semplice rosso e impostare Stato magazzino su *In magazzino*, quindi imposta lo stato Abilita prodotto su *No*.
1. Imposta l’inventario del prodotto semplice Brown, quindi imposta lo stato Abilita prodotto su *Sì*.
1. Assicurati che lo stato del magazzino del prodotto configurabile sia *In magazzino*.
1. Modificare l&#39;inventario del prodotto semplice Marrone su 0 e impostare lo stato del magazzino su *Esaurito*.
1. A questo punto, lo stato del magazzino del prodotto configurabile è ancora *In magazzino*.
1. Eseguire la reindicizzazione.
1. Controlla la `min_price` e `max_price` per il prodotto configurabile in `catalog_product_index_price` Tabella DB: i due valori sono impostati su 0.
1. Ma se impostiamo lo stato del magazzino del prodotto configurabile su *Esaurito* e poi reindicizziamo, vediamo un valore diverso da zero `min_price` e `max_price` valori del prodotto configurabile.

<u>Risultati previsti</u>:

Se tutti i prodotti secondari *Esaurito* e il prodotto configurabile stesso è *Esaurito*, il prezzo viene calcolato utilizzando tutti i prodotti secondari.

<u>Risultati effettivi</u>:

Il `min_price` e `max_price` valori per il prodotto configurabile in `catalog_product_index_price` La tabella DB è impostata su 0 quando lo stato delle scorte configurabile è *In magazzino*, ma se è *Esaurito* diventano valori diversi da zero.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
