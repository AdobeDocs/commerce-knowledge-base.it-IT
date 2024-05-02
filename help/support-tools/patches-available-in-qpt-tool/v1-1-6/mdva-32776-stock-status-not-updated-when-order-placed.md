---
title: "MDVA-32776: stato del magazzino non aggiornato con il posizionamento dell'ordine"
description: La patch MDVA-32776 risolve il problema che causa l'aggiornamento dello stato delle scorte quando un ordine viene effettuato ma non spedito. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.6. L'ID della patch è MDVA-32776. Il problema è stato risolto in Adobe Commerce 2.4.2.
exl-id: 10e9458f-562a-480b-b813-104a93db4308
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-32776: lo stato del magazzino non viene aggiornato con l&#39;inserimento dell&#39;ordine

La patch MDVA-32776 risolve il problema che causa l&#39;aggiornamento dello stato delle scorte quando un ordine viene effettuato ma non spedito. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.6. L&#39;ID della patch è MDVA-32776. Il problema è stato risolto in Adobe Commerce 2.4.2.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.0

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.1-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Lo stato delle scorte non viene aggiornato quando un ordine viene effettuato ma non spedito.

<u>Prerequisiti</u>:

1. Il modulo Inventario è installato.
1. Visualizza prodotti esauriti è impostato su *Sì*.

   Per impostare, vai a **Negozi** > **Configurazione** > **Catalogo** > **Inventario** > **Visualizza prodotti esauriti** = *Sì*.

<u>Passaggi da riprodurre</u>:

1. Creare due prodotti semplici con qtà = 11 e 22.
1. Crea un prodotto raggruppato utilizzando i prodotti semplici creati nel primo passaggio.
1. Aggiungere prodotti raggruppati al carrello impostando una delle quantità di prodotto su 11 e facendo esaurire l&#39;altro prodotto semplice.
1. Completa il pagamento e fai l’ordine.

<u>Risultati previsti</u>:

Visualizzazione prodotti raggruppati `out-of-stock` etichette quando i prodotti semplici associati escono dallo stock.

<u>Risultati effettivi</u>:

1. Il prodotto semplice con qtà = 11 è esaurito.
1. Il prodotto raggruppato non mostra un *esaurito* messaggio per il prodotto con qtà = 11. Tuttavia, l’aggiunta di questo prodotto al carrello offre *esaurito* errore.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sezione.
