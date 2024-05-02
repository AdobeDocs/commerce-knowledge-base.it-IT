---
title: Visualizzazione del livello vCPU dell’ambiente nel cluster in Adobe Commerce
promoted: true
description: Questo articolo spiega come controllare l’allocazione a livello vCPU utilizzando la scheda New Relic Infra su Osservazione per Adobe Commerce. Observation for Adobe Commerce è un nerdlet di New Relic che mostra lo stato del sito Adobe Commerce e le visualizzazioni del tempo corrente e passato.
exl-id: a0332e7e-d38d-47d3-b3da-293902f45edc
source-git-commit: 309fda5284de3b8be54e95bf2bfd8ff1777b6c90
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# Visualizzazione del livello vCPU dell’ambiente nel cluster in Adobe Commerce

Questo articolo spiega come controllare l’allocazione a livello vCPU utilizzando la scheda New Relic Infra su Osservazione per Adobe Commerce. Observation for Adobe Commerce è un nerdlet di New Relic che mostra lo stato del sito Adobe Commerce e le visualizzazioni del tempo corrente e passato.

## Prodotti e versioni interessati:

Adobe Commerce sull’infrastruttura cloud 2.4.3 - 2.4.6

## Controllare l’allocazione a livello vCPU con Osservazione per Adobe Commerce:

Per accedere al nerdlet New Relic Observation for Adobe Commerce:

1. Dalla pagina Home di New Relic, fai clic su **App**.
1. Clic **Osservazione per Adobe Commerce**.
1. Viene aperto il nerdlet Observation for Adobe Commerce.
1. Fai clic sul pulsante **Seleziona un account** e selezionare un account.
1. Puoi inserire l’ID del progetto, il numero di account New Relic o il nome dell’account, oppure sfogliare l’elenco degli account.
1. Fai clic sul menu a discesa azzurro con l’icona dell’orologio (in alto a destra nella finestra del nerdlet).
1. Se stai tentando di identificare la causa di un evento/problema, seleziona un’ora prima della data e dell’ora del ticket per verificare se vi sono stati eventi/dati precedenti. È possibile utilizzare gli intervalli di tempo predefiniti o impostare un intervallo di tempo personalizzato selezionando **Imposta personalizzato**.
1. Nelle schede fai clic su **Infra**. Sono disponibili tre grafici a livello vCPU:
   * Il primo grafico mostra **Visualizzazione a livello vCPU su timeline MAGGIORE di 2 settimane (è necessario selezionare una timeline MAGGIORE di 2 settimane). NOTA: il tasso di campionamento sarà giornaliero. Se in un giorno si verificano upsize/downsize del cluster, le dimensioni del livello finale verranno visualizzate il giorno successivo**.
   * Il secondo grafico mostra **Vista a livello vCPU sulla timeline (è necessario selezionare una timeline maggiore di 24 ore ma non maggiore di 2 settimane)**.
   * Il terzo grafico mostra **La vista a livello vCPU sulla timeline BY NODE dovrebbe esaminare la timeline MENO di 24 ore**.

## Lettura correlata

* [Panoramica di Observation for Adobe Commerce](/help/support-tools/observation-for-adobe-commerce/observation-adobe-commerce-overview.md) nella nostra knowledge base di supporto.
