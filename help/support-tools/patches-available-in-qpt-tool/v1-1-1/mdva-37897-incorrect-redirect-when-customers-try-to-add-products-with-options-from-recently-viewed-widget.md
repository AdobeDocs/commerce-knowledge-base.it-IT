---
title: 'MDVA-37897: reindirizzamento non corretto quando si aggiungono prodotti visualizzati di recente'
description: La patch MDVA-37897 risolve il problema del reindirizzamento errato quando gli utenti tentano di aggiungere prodotti con opzioni del widget Visualizzato di recente. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1. L'ID della patch è MDVA-37897. Il problema è pianificato per la risoluzione in Adobe Commerce versione 2.4.4.
exl-id: f0a86e02-b357-4d2d-8386-e9cc045bcf06
feature: Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# MDVA-37897: reindirizzamento non corretto quando si aggiungono prodotti visualizzati di recente

La patch MDVA-37897 risolve il problema del reindirizzamento errato quando gli utenti tentano di aggiungere prodotti con opzioni del widget Visualizzato di recente. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1. L&#39;ID della patch è MDVA-37897. Il problema è pianificato per la risoluzione in Adobe Commerce versione 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce sulla nostra infrastruttura cloud 2.4.1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.2-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando un utente tenta di aggiungere un prodotto dalla sezione Visualizzato di recente in cui è necessario selezionare alcune opzioni, viene reindirizzato alla pagina dell’elenco dei prodotti anziché alla pagina dei dettagli del prodotto.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto semplice con opzioni personalizzabili (Tipo: Pulsante di scelta).
1. Configura il widget Visualizzato di recente per mostrare i prodotti.
1. Visita i prodotti con opzioni personalizzabili in modo che vengano visualizzati nel widget Visualizzato di recente.
1. Fai clic su **Aggiungi al carrello** su uno dei prodotti nel widget Visualizzato di recente.

<u>Risultati previsti</u>:

Ti reindirizzano alla pagina dei dettagli del prodotto per scegliere le opzioni.

<u>Risultati effettivi</u>:

Ti reindirizzano alla pagina dell’elenco dei prodotti.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti a seconda del tipo di distribuzione:

* Adobe Commerce on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sulla nostra infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sulle patch di qualità per Adobe Commerce, consulta:

* [È stato rilasciato lo strumento Quality Patches: è stato introdotto un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
