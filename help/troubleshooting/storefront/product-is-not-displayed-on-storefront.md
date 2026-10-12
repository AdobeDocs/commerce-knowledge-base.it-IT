---
title: Il prodotto non viene visualizzato nella vetrina
description: Questo articolo fornisce soluzioni per i casi in cui i prodotti non vengono visualizzati nella vetrina.
exl-id: 454eca5b-4722-46e0-8e5d-3daf8e3e675a
feature: Cache, Categories, Console, Products, Storefront
role: Admin
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
  - id: c4af0798-d497-5e6b-8380-19812c26d00a
    internal-label: Console
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%
---
# Il prodotto non viene visualizzato nella vetrina

Questo articolo fornisce soluzioni per i casi in cui i prodotti non vengono visualizzati nella vetrina.

## Prodotti e versioni interessati

* Adobe Commerce on-premise X.X.X
* Adobe Commerce su infrastruttura cloud X.X.X

## Problema

<u>Passaggi da riprodurre</u>:

1. Accedi all’amministratore di Commerce.
1. Vai a **Catalogo** > **Prodotti**.

   ![open_product_page_magento_2.4.1.png](assets/open_product_page_magento_2.4.1.png)

1. Fai clic su **Aggiungi prodotto** e segui il processo di creazione del prodotto. Oppure importa prodotti da un file CSV.

<u>Risultato previsto</u>:

Il prodotto viene visualizzato nella vetrina.

<u>Risultato effettivo</u>:

Il prodotto non viene visualizzato.

## Causa

Ciò può essere dovuto a diversi motivi. Segui i passaggi riportati di seguito per verificare i punti principali utili per identificare e risolvere il problema.

## Soluzione

Ciascuno dei seguenti punti potrebbe risolvere il problema.

* Controlla le impostazioni del prodotto in Admin. Vai a **Catalogo** > **Prodotti**, apri la pagina del prodotto e assicurati che i seguenti campi siano configurati correttamente:
  * **Abilita prodotto** = *Sì.*
  * **Stato Stock**: *In Stock*. Oppure se *Esaurito* è il valore corretto, assicurarsi che **Visualizza prodotti esauriti** (**ARCHIVI** > **Impostazioni** > **Configurazione** > **CATALOGO** > **Inventario** > **Opzioni magazzino** > **Visualizza prodotti esauriti**) sia impostato su *Sì* (configurato a livello globale).
  * **Categorie**: se tenti di trovare il prodotto in una pagina della categoria, verifica che il prodotto sia assegnato alla categoria. Per semplificare la risoluzione dei problemi, crea una nuova categoria dalla pagina corrente e assegna un prodotto.
  * **Visibilità** = *Catalogo, Ricerca.*
  * Nella sezione **Prodotto in siti Web**, assicurati che il prodotto sia assegnato al sito Web corretto.
  * Passa il selettore dell&#39;ambito alla visualizzazione dello store in cui si tenta di trovare il prodotto nella vetrina e verifica le stesse impostazioni.
* Eseguire la reindicizzazione completa eseguendo `bin/magento indexer:reindex` dalla console e svuotare tutta la cache dell&#39;amministratore in **Sistema** > **Strumenti** > **Gestione cache** oppure dalla console eseguendo `bin/magento cache:clean`.
* Se quanto sopra non aiuta, è possibile avviare ulteriori indagini controllando i registri nella directory `var/log`.



