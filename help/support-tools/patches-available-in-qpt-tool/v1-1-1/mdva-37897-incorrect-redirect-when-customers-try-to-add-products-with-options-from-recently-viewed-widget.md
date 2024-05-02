---
title: "MDVA-37897: reindirizzamento non corretto quando si aggiungono prodotti visualizzati di recente"
description: La patch MDVA-37897 risolve il problema del reindirizzamento errato quando gli utenti tentano di aggiungere prodotti con opzioni del widget Visualizzato di recente. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1. L'ID della patch è MDVA-37897. Il problema è pianificato per la risoluzione in Adobe Commerce versione 2.4.4.
exl-id: f0a86e02-b357-4d2d-8386-e9cc045bcf06
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# MDVA-37897: reindirizzamento non corretto quando si aggiungono prodotti visualizzati di recente

La patch MDVA-37897 risolve il problema del reindirizzamento errato quando gli utenti tentano di aggiungere prodotti con opzioni del widget Visualizzato di recente. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1. L&#39;ID della patch è MDVA-37897. Il problema è pianificato per la risoluzione in Adobe Commerce versione 2.4.4.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce sulla nostra infrastruttura cloud 2.4.1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.2-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando un utente tenta di aggiungere un prodotto dalla sezione Visualizzato di recente in cui è necessario selezionare alcune opzioni, viene reindirizzato alla pagina dell’elenco dei prodotti anziché alla pagina dei dettagli del prodotto.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto semplice con opzioni personalizzabili (Tipo: Pulsante di scelta).
1. Configura il widget Visualizzato di recente per mostrare i prodotti.
1. Visita i prodotti con opzioni personalizzabili in modo che vengano visualizzati nel widget Visualizzato di recente.
1. Clic **Aggiungi al carrello** su uno dei prodotti nel widget Visualizzato di recente.

<u>Risultati previsti</u>:

Ti reindirizzano alla pagina dei dettagli del prodotto per scegliere le opzioni.

<u>Risultati effettivi</u>:

Ti reindirizzano alla pagina dell’elenco dei prodotti.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti a seconda del tipo di distribuzione:

* Adobe Commerce on-premise: [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sulla nostra infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sulle patch di qualità per Adobe Commerce, consulta:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sezione.
