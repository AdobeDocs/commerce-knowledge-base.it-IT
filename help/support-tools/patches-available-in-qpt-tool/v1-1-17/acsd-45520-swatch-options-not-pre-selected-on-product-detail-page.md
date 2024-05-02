---
title: "ACSD-45520: opzioni campione non selezionate nella pagina dei dettagli del prodotto"
description: La patch ACSD-45520 risolve il problema per cui le opzioni dei campioni non sono preselezionate nella pagina dei dettagli del prodotto quando un utente modifica prodotti configurabili dal carrello. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17. L’ID della patch è ACSD-45520. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.
exl-id: 941f4a45-bc3c-44c0-a582-ddfe179fa8c3
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# ACSD-45520: opzioni campione non selezionate nella pagina dei dettagli del prodotto

La patch ACSD-45520 risolve il problema per cui le opzioni dei campioni non sono preselezionate nella pagina dei dettagli del prodotto quando un utente modifica prodotti configurabili dal carrello. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17. L’ID della patch è ACSD-45520. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le opzioni Campione non sono selezionate nella pagina dei dettagli del prodotto quando un utente modifica dal carrello i prodotti configurabili.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto configurabile con opzioni di prodotto (ad es. colore).
1. Aggiungi il prodotto configurabile al carrello.
1. Vai alla pagina Il mio carrello.
1. Fai clic sul pulsante Modifica sul prodotto configurabile aggiunto al passaggio 1.
1. Osserva le opzioni del prodotto nella pagina di modifica.

<u>Risultati previsti</u>:

Le opzioni prodotto sono selezionate.

<u>Risultati effettivi</u>:

Le opzioni prodotto non sono selezionate.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
