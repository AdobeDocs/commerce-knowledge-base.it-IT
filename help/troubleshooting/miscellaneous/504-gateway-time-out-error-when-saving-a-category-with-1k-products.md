---
title: Errore di timeout del gateway 504 durante il salvataggio di una categoria con più di 1k prodotti
description: Questo articolo suggerisce una soluzione per il problema di timeout che potrebbe verificarsi quando si eseguono operazioni con categorie di grandi dimensioni (1k+ prodotti).
exl-id: 1f4b0385-215d-4d3d-8704-986c090824aa
feature: Cache, Categories, Marketing Tools, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# Errore di timeout del gateway 504 durante il salvataggio di una categoria con più di 1k prodotti

Questo articolo suggerisce una soluzione per il problema di timeout che potrebbe verificarsi quando si eseguono operazioni con categorie di grandi dimensioni (1k+ prodotti).

## Prodotti e versioni interessati:

* Adobe Commerce sull’infrastruttura cloud 2.3.3
* Adobe Commerce on-premise 2.3.3
* Magento Open Source 2.3.3

## Problema

Prerequisiti: **Negozi** > **Configurazione** > **CATALOGO** > **Catalogo** > **Usa il percorso delle categorie per gli URL dei prodotti** è impostata su *Sì* per la visualizzazione store.

<u>Passaggi da riprodurre</u>

1. In Commerce Admin, vai a **Catalogo** > **Categorie**.
1. Apri una categoria grande, ad esempio più di 1000 prodotti assegnati.
1. Aggiungi un prodotto alla categoria.
1. Clic **Salva categoria**.

<u>Risultato previsto:</u>

Categoria salvata correttamente.

<u>Risultato effettivo:</u>

Dopo cinque minuti di salvataggio del processo, viene visualizzata la pagina di errore di timeout del gateway 504.

## Causa

Il processo richiede più tempo del timeout configurato dal server.

## Soluzione

Disattivazione di **Genera riscritture URL &quot;categoria/prodotto&quot;** rimuoverà tutte le riscritture URL di categoria/prodotto dal database e ridurrà significativamente il tempo necessario per le operazioni con le categorie grandi.

>[!WARNING]
>
>Se questa opzione viene disattivata, la rimozione permanente delle riscritture degli URL di categoria/prodotto non sarà più possibile ripristinarle.

Per disattivare **Genera riscritture URL &quot;categoria/prodotto&quot;** opzione:

1. In Amministrazione Commerce, passa a **Negozi** > **Configurazione** > **CATALOGO** > **Catalogo**.
1. Nell&#39;angolo in alto a sinistra della pagina di configurazione, nel **Ambito** , imposta l&#39;ambito di configurazione su *Configurazione predefinita*.
1. Imposta **Genera riscritture URL &quot;categoria/prodotto&quot;** a *No*.
1. Clic **Salva configurazione**.
1. Pulisci cache eseguendo    ```bash    bin/magento cache:clean    ```    o in Commerce Admin in **Sistema** > **Strumenti** > **Gestione cache**.

Ora è possibile aggiungere prodotti alle categorie o spostare le categorie con un numero elevato di prodotti. Queste operazioni richiederanno molto meno tempo e non dovrebbero causare timeout.

## Lettura correlata

[Reindirizzamenti automatici dei prodotti](https://docs.magento.com/user-guide/v2.3/marketing/url-redirect-product-automatic.html) nella guida utente.
