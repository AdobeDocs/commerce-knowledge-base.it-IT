---
title: Errore di timeout del gateway 504 durante il salvataggio di una categoria con più di 1k prodotti
description: Questo articolo suggerisce una soluzione per il problema di timeout che potrebbe verificarsi quando si eseguono operazioni con categorie di grandi dimensioni (1k+ prodotti).
exl-id: 1f4b0385-215d-4d3d-8704-986c090824aa
feature: Cache, Categories, Marketing Tools, Products
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

Prerequisiti: l&#39;opzione **Archivi** > **Configurazione** > **CATALOGO** > **Catalogo** > **Usa percorso categorie per URL prodotto** è impostata su *Sì* per la visualizzazione archivio.

<u>Passaggi da riprodurre</u>

1. In Amministrazione Commerce, vai a **Catalogo** > **Categorie**.
1. Apri una categoria grande, ad esempio più di 1000 prodotti assegnati.
1. Aggiungi un prodotto alla categoria.
1. Fai clic su **Salva categoria**.

<u>Risultato previsto:</u>

Categoria salvata correttamente.

<u>Risultato effettivo:</u>

Dopo cinque minuti di salvataggio del processo, viene visualizzata la pagina di errore di timeout del gateway 504.

## Causa

Il processo richiede più tempo del timeout configurato dal server.

## Soluzione

Se si disabilita l&#39;opzione **Genera URL &quot;categoria/prodotto&quot; Riscrittura**, verranno rimosse dal database tutte le riscritture degli URL di categoria/prodotto e verrà ridotto in modo significativo il tempo necessario per le operazioni con categorie di grandi dimensioni.

>[!WARNING]
>
>Se questa opzione viene disattivata, la rimozione permanente delle riscritture degli URL di categoria/prodotto non sarà più possibile ripristinarle.

Per disabilitare l&#39;opzione **Genera URL &quot;categoria/prodotto&quot; Riscrive**:

1. In Amministrazione Commerce, passa a **Archivi** > **Configurazione** > **CATALOGO** > **Catalogo**.
1. Nell&#39;angolo superiore sinistro della pagina di configurazione, nel campo **Ambito**, imposta l&#39;ambito di configurazione su *Configurazione predefinita*.
1. Impostare **Genera URL &quot;categoria/prodotto&quot; Riscrive** in *No*.
1. Fai clic su **Salva configurazione**.
1. Pulisci cache eseguendo    ```bash    bin/magento cache:clean    ```    o nell&#39;amministratore di Commerce in **Sistema** > **Strumenti** > **Gestione cache**.

Ora è possibile aggiungere prodotti alle categorie o spostare le categorie con un numero elevato di prodotti. Queste operazioni richiederanno molto meno tempo e non dovrebbero causare timeout.

## Lettura correlata

[Reindirizzamenti automatici ai prodotti](https://experienceleague.adobe.com/it/docs/commerce-admin/marketing/seo/url-rewrites/url-redirect-product-automatic) nella guida utente.
