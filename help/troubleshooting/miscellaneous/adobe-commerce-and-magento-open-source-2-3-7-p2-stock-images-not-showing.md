---
title: Immagini d'archivio non visualizzate, Adobe Commerce e Magento Open Source 2.3.7-p2
description: Questo articolo fornisce una soluzione per il problema in cui le immagini stock di Adobi caricate nelle directory del file system "pub/media" o "pub/media/catalog" non vengono visualizzate nell’interfaccia utente di Media Gallery. Le immagini non rientrano nelle directory della raccolta multimediale consentite. Affinché queste immagini possano essere visualizzate, i commercianti devono eliminare le immagini nel file system e ricaricarle in una directory Media Gallery consentita.
exl-id: 84488d87-095f-4739-858f-19a52d6e5822
feature: Categories, Orders
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# Immagini d&#39;archivio non visualizzate, Adobe Commerce e Magento Open Source 2.3.7-p2

In questo articolo viene fornita una soluzione al problema che impedisce la visualizzazione delle immagini Adobi caricate nelle directory del file system `pub/media` o `pub/media/catalog` nell&#39;interfaccia utente di Media Gallery. Le immagini non rientrano nelle directory della raccolta multimediale consentite. Affinché queste immagini possano essere visualizzate, i commercianti devono eliminare le immagini nel file system e ricaricarle in una directory Media Gallery consentita.

## Prodotti e versioni interessati

* Adobe Commerce e Magento Open Source 2.3.7-p2


## Problema

Gli esercenti possono caricare le immagini Adobe Stock nella directory principale dell’archiviazione in Media Gallery, ma non vengono visualizzate nell’interfaccia utente e appariranno come se non fossero state caricate. Questo perché il sistema nota che l’immagine è già caricata nel file system, anche se non è disponibile nell’interfaccia utente di Media Gallery. Ciò significa che una volta che un commerciante carica un&#39;immagine in `pub/media` o `pub/media/catalog`, non può utilizzarla finché non viene eliminata direttamente nel file system.

<u>Passaggi da riprodurre</u>

1. Abilita Adobe Stock con chiavi API valide.
1. Apri la raccolta multimediale (**Catalogo** > **Categorie** > **Contenuto** sezione > fai clic su **Seleziona dalla raccolta**).
1. Fare clic su **Cerca in Adobe Stock**.
1. Seleziona un’immagine. Fare clic su **Salva anteprima**. Per visualizzare le immagini potrebbe essere necessario reimpostare la griglia di Adobe Stock.

<u>Risultato previsto</u>:

Viene visualizzata l’immagine.

<u>Risultato effettivo</u>:

Viene visualizzato un messaggio di errore: *Impossibile individuare l&#39;immagine. Impossibile trovare l&#39;immagine nella raccolta multimediale.*

## Causa

Le immagini possono essere caricate nella directory principale di archiviazione di Media Gallery tramite Adobe Stock.

## Soluzione

Seleziona una sottodirectory della directory principale di archiviazione di Media Gallery (escluso **Directory principale di archiviazione** > **Catalogo**) prima di caricare un&#39;immagine Adobe Stock.
Elimina le immagini Adobe Stock caricate dalle cartelle `pub/media` e `pub/media/catalog` nel file system di Adobe Commerce e carica le immagini nelle sottodirectory radice di archiviazione di Media Gallery consentite (escluso **Directory principale di archiviazione** > **Catalogo**).

## Lettura correlata

* [Archiviazione multimediale](https://docs.magento.com/user-guide/v2.3/cms/media-storage.html) nella guida utente.
