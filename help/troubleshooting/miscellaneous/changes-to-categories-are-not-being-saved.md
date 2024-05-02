---
title: Le modifiche alle categorie non vengono salvate
description: 'Questo articolo corregge alcuni problemi che si verificavano durante l’aggiornamento delle categorie di prodotti tramite l’amministratore di Commerce: le modifiche non venivano visualizzate nell’amministratore e nella vetrina. Il problema è causato dai dati danneggiati nella tabella "catalog_category_entity". Per risolvere il problema, correggere o rimuovere i record di aggiornamento delle categorie problematici nella tabella. Dopodiché, dovresti essere in grado di aggiornare le categorie di prodotto utilizzando l’Amministratore.'
exl-id: d951205c-add9-478c-9c7d-2ba975d53b14
feature: Categories
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '721'
ht-degree: 0%

---

# Le modifiche alle categorie non vengono salvate

Questo articolo corregge alcuni problemi che si verificavano durante l’aggiornamento delle categorie di prodotti tramite l’amministratore di Commerce: le modifiche non venivano visualizzate nell’amministratore e nella vetrina. Il problema è causato dal danneggiamento dei dati in `catalog_category_entity` tabella. Per risolvere il problema, correggere o rimuovere i record di aggiornamento delle categorie problematici nella tabella. Dopodiché, dovresti essere in grado di aggiornare le categorie di prodotto utilizzando l’Amministratore.

## Problema

Dopo aver apportato modifiche a una categoria di prodotto nell’amministratore e aver salvato, i nuovi aggiornamenti non vengono salvati né visualizzati nell’amministratore e nella vetrina.

### Passaggi da riprodurre

1. Vai a **Catalogo** > **Categorie**.
1. Seleziona una categoria.
1. Apporta le modifiche, quindi fai clic su **Salva**.
1. Viene visualizzato il messaggio: *Categoria salvata*.
1. Nota che la modifica apportata non è stata salvata.

## Possibile causa: dati danneggiati nel `catalog_category_entity` tabella

Il problema è causato dagli stessi valori in `created_in` colonna dei record delle categorie interessate nel database (DB).

![Dati danneggiati nella tabella catalog_category_entity](assets/catalog_category_entity.png)

Dettagli:

* Il `catalog_category_entity` La tabella DB contiene due o più record per la categoria interessata (questi record hanno lo stesso `entity_id` valore).
* Questi record di categoria hanno **gli stessi valori in `created_in` colonna**.

### Come viene visualizzata la seconda voce del database (e tutte le successive) nel database per una sola e stessa categoria?

Il secondo record DB (ed eventualmente i successivi) per la categoria interessata indica che sono stati pianificati aggiornamenti di categoria utilizzando il modulo Magento\_Staging. Il modulo crea un record aggiuntivo per una categoria nella `catalog_category_entity` e questo è il comportamento previsto dell&#39;applicazione; il problema è che i record hanno gli stessi valori per `created_in` colonna.

### Come vengono visualizzati gli stessi valori?

Non possiamo spiegare con certezza le ragioni della corruzione dei dati. I possibili motivi possono includere:

* personalizzazioni (codice, temi, ecc.)
* migrazione dei dati non corretta
* ripristino dati errato dal backup

A nostra conoscenza, tale danneggiamento dei dati non è tipico dell’istanza Adobe Commerce &quot;pulita&quot; (preconfigurata) e non può essere riprodotto su un’installazione Adobe Commerce senza personalizzazioni.

### Come verificare che questo sia il tuo problema

Il `catalog_category_entity` la tabella deve avere più record per la categoria interessata (i record devono avere lo stesso `entity_id` e almeno due di tali record devono avere lo stesso `created_in` valori. In questo modo, gli aggiornamenti pianificati per la gestione temporanea non verranno visualizzati nell’amministratore di Commerce; verrà visualizzato solo il blocco Modifiche pianificate vuoto.

#### Passaggi da verificare

1. Accedere alla tabella catalog\_category\_entity nel database.
1. Filtra le entità per entity\_id, con entity\_id che identifica la categoria interessata.
1. Se i valori nella colonna\_in creata sono gli stessi per voci diverse con la stessa entità\_id, questo è il nostro caso. Normalmente, il `created_in` I valori sono diversi per ogni record.

![Dati danneggiati nella tabella catalog_category_entity](assets/catalog_category_entity.png)

## Soluzione

Puoi scegliere una delle seguenti soluzioni:

1. **Elimina** record di aggiornamento categoria problematici
1. **Ripara** record di aggiornamento categoria problematici

### Eliminare i record di aggiornamento delle categorie problematici

In questa soluzione, sarà necessario impostare il `updated_in` valore per il record categoria iniziale ed eliminare tutti gli altri record per questa categoria. Verranno rimossi tutti gli aggiornamenti delle categorie pianificati.

Segui questi passaggi:

1. Trovare i record DB con `entity_id` della categoria interessata.
1. Selezionare il record con il numero intero più grande nella `updated_in` colonna.
1. Copia il `updated_in` valore dal record selezionato.
1. Seleziona il record con `row_id` = `entity_id` (record categoria iniziale) e incolla il valore copiato nel `updated_in` colonna di questo record.
1. Elimina righe con `row_id` non uguale a `entity_id` .

### Ripristinare i record di aggiornamento delle categorie problematici

1. Trovare i record categoria con lo stesso `entity_id` e lo stesso `created_in` valore.
1. Selezionare il record in cui `row_id` = `entity_id` e copia `updated_in` valore.
1. Selezionare il record in cui `row_id` non è uguale a `entity_id` e incolla la copia `updated_in` valore come `created_in` valore. Vedi la schermata seguente come illustrazione.    ![Copiare il file value_in creato.png](assets/copy_created-in_value.png)
1. Verificare che il record di aggiornamento della categoria, il `created_in` il cui valore è stato aggiornato (nel passaggio 3), esiste nel `staging_update` tabella. *Ad esempio:* SE la copia `created_in` valore è 1509281953, THEN l’entità con `row_id` = 1509281953 deve esistere nel `staging_update` tabella
