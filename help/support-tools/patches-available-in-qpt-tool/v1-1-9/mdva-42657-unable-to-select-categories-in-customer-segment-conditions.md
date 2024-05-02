---
title: "MDVA-42657: impossibile selezionare le categorie nelle condizioni del segmento del cliente"
description: La patch MDVA-42657 risolve il problema che impediva all'utente amministratore di selezionare le categorie nelle condizioni del segmento cliente. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9. L'ID della patch è MDVA-42657. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: 9c810dcd-b39b-4456-a362-5452ada4dc53
feature: Categories, Console, Customer Service
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# MDVA-42657: impossibile selezionare le categorie nelle condizioni del segmento cliente

La patch MDVA-42657 risolve il problema che impediva all&#39;utente amministratore di selezionare le categorie nelle condizioni del segmento cliente. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9. L&#39;ID della patch è MDVA-42657. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’utente amministratore non è in grado di selezionare le categorie nelle condizioni del segmento cliente.

<u>Passaggi da riprodurre</u>:

1. Vai a **Clienti** > **Segmenti**.
1. Crea un nuovo segmento.
1. Vai al segmento appena creato e fai clic su **Condizioni** nel menu di navigazione a sinistra.
1. Fare clic sul segno più verde.
1. Seleziona Cronologia prodotto in Prodotti.
1. Cambia &quot;visualizzato&quot; in &quot;ordinato&quot;.
1. Modificare &quot;ALL&quot; in &quot;ANY&quot;.
1. Fai clic sul segno più verde nidificato e seleziona Categoria.
1. Fai clic su **...** fai clic sull’icona del selettore (a sinistra del segno di spunta).
1. Apri la console di sviluppo del browser.
1. Seleziona le caselle di controllo per una o più categorie e annota l’errore JavaScript generato nella console.
1. Fai clic su **Salva** pulsante.
1. Torna alla condizione e controlla se le categorie selezionate sono salvate.

<u>Risultati previsti</u>:

Le categorie selezionate vengono salvate e selezionate durante la visualizzazione o la modifica delle condizioni del segmento.

<u>Risultati effettivi</u>:

Le categorie selezionate risultano mancanti e non sono state salvate correttamente. Nella console viene visualizzato il seguente errore:

```
category-checkbox-tree.js:249 Uncaught TypeError: Cannot set properties of undefined (setting 'value')
    at Ext.tree.TreePanel.Enhanced.<anonymous> (category-checkbox-tree.js:249)
    at Ext.util.Event.fire (ext-tree.js:29)
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
