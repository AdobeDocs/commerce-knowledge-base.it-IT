---
title: "Patch MDVA-30593: le virgolette scadute non vengono pulite"
description: La patch MDVA-30593 risolve il problema che impedisce la pulizia delle virgolette scadute in base all'impostazione **Quote Lifetime**. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5. Il problema è stato risolto in Adobe Commerce 2.3.4.
exl-id: 5ee91546-a5cb-4282-bdfc-c9bb3438af50
feature: Cache, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# Patch MDVA-30593: le virgolette scadute non vengono pulite

La patch MDVA-30593 risolve il problema che impedisce la pulizia delle virgolette scadute in base all&#39;impostazione **Durata offerta**. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5. Il problema è stato risolto in Adobe Commerce 2.3.4.

## Prodotti e versioni interessati

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0-2.3.3.x

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le virgolette scadute in base all&#39;impostazione **Durata offerta** non vengono pulite.

<u>Passaggi da riprodurre:</u>

1. In Amministrazione Commerce, vai a **Negozi** > **Configurazione** > **Vendite** > **Pagamento** > **Carrello acquisti**.
1. Imposta **Durata offerta (giorni)** = *1*
1. Salva la configurazione e cancella la cache.
1. Accedi come cliente.
1. Aggiungi un prodotto al carrello.
1. Dopo un giorno, torna al carrello.

<u>Risultato previsto:</u>

Il preventivo viene cancellato e il prodotto viene rimosso dal carrello, poiché il prezzo precedente non è più valido.

<u>Risultato effettivo:</u>

Il prodotto è ancora nel carrello.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
