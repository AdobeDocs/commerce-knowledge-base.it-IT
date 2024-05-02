---
title: Il prodotto non viene visualizzato nella vetrina
description: Questo articolo fornisce soluzioni per i casi in cui i prodotti non vengono visualizzati nella vetrina.
exl-id: 454eca5b-4722-46e0-8e5d-3daf8e3e675a
feature: Cache, Categories, Console, Products, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '344'
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

1. Clic **Aggiungi prodotto** e segui il processo di creazione del prodotto. Oppure importa prodotti da un file CSV.

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
   * **Stato Stock**: *In magazzino*. Oppure se *Esaurito* è il valore corretto, assicurati che **Visualizza prodotti esauriti** (**NEGOZI** > **Impostazioni** > **Configurazione** > **CATALOGO** > **Inventario** > **Opzioni Stock** > **Visualizza prodotti esauriti**) è impostato su *Sì* (configurata a livello globale).
   * **Categorie**: se tenti di trovare il prodotto in una pagina di categoria, verifica che il prodotto sia assegnato alla categoria. Per semplificare la risoluzione dei problemi, crea una nuova categoria dalla pagina corrente e assegna un prodotto.
   * **Visibilità** = *Catalogo, Ricerca.*
   * In **Prodotto nei siti Web** , assicurati che il prodotto sia assegnato al sito web corretto.
   * Passa il selettore dell&#39;ambito alla visualizzazione dello store in cui si tenta di trovare il prodotto nella vetrina e verifica le stesse impostazioni.
* Eseguire la reindicizzazione completa eseguendo `bin/magento indexer:reindex` dalla console ed esegui il flushing di tutta la cache in Admin, in **Sistema** > **Strumenti** > **Gestione cache**, o dalla console eseguendo `bin/magento cache:clean`.
* Se quanto sopra non aiuta, puoi avviare ulteriori indagini controllando i registri in `var/log` directory.

## Lettura correlata nella knowledge base del supporto

* [Posizioni di registro (directory) per l’architettura Pro](/help/how-to/general/log-locations-directories-for-pro-plan-integration-staging-production.md)
* [Posizioni di registro (directory) per l’architettura Starter](/help/how-to/general/log-locations-directories-for-starter-plan.md)
