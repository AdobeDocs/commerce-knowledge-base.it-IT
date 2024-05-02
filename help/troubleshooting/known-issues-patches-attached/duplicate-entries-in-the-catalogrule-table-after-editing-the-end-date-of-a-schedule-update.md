---
title: Voci duplicate nella tabella catalogrule dopo la modifica della data di fine di un aggiornamento della pianificazione
description: Questo articolo fornisce una patch per il problema noto di Adobe Commerce 2.2.3 in cui la modifica della data o dell’ora di fine di un aggiornamento della pianificazione di una regola del prezzo di catalogo determina l’aggiunta di voci duplicate alla tabella "catalogrule" ed errori nella reindicizzazione dell’indicizzatore "catalogrule_rule" (prodotto regola catalogo).
exl-id: e900b712-d0f5-4404-8441-64522035ce44
feature: Cache, Catalog Management, Marketing Tools
role: Developer
source-git-commit: 496151d1fe29a66d84349e4a96e7c5563a92c5c4
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---

# Voci duplicate nella tabella catalogrule dopo la modifica della data di fine di un aggiornamento della pianificazione

Questo articolo fornisce una patch per il problema noto di Adobe Commerce 2.2.3 in cui la modifica della data o dell’ora di fine di un aggiornamento della pianificazione di una regola del prezzo di catalogo determina l’aggiunta di voci duplicate alla `catalogrule` tabella ed errori in `catalogrule_rule` Reindicizzazione dell’indicizzatore (prodotto regola catalogo).

## Problema

Quando si modifica la data o l&#39;ora di fine di un aggiornamento esistente della programmazione di una regola del prezzo di catalogo, vengono creati dati duplicati in `catalogrule` tabella di database. Di conseguenza, il `catalogrule_rule` la reindicizzazione non riesce e viene visualizzato il seguente errore nel registro eccezioni: *Esiste già un elemento con lo stesso ID*.

<u>Passaggi da riprodurre</u>:

Prerequisiti: `catalogrule_rule` indicizzatore impostato su *[Aggiorna secondo programma](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/indexer-configuration.html)* modalità.

1. Nell’amministratore di Commerce, crea una nuova regola di prezzo catalogo in **Marketing** > **Promozioni** > **Regola prezzo catalogo**.
1. In **Regola prezzo catalogo** griglia, fare clic su **Modifica**, e pianifica un nuovo aggiornamento e imposta **Stato** a *Attivo.*
1. Clic **Visualizza/Modifica** accanto al nuovo aggiornamento creato e modificare la data di fine in un&#39;ora precedente.
1. Salva l&#39;aggiornamento.
1. Esegui il comando reindex per `catalogrule_rule` indicizzatore.

<u>Risultato previsto</u>:

Il `catalogrule_rule` indicizzatore reindicizzato correttamente. Nessuna voce duplicata nel `catalogrule` tabella.

<u>Risultato effettivo</u>:

La reindicizzazione non riesce e viene visualizzato il seguente errore: *Esiste già un elemento con lo stesso ID*, perché sono presenti voci duplicate nel `catalogrule` tabella.

## Soluzione

Per risolvere il problema è necessario applicare la patch allegata e rimuovere le voci duplicate esistenti. Consulta la [Rimuovi le voci duplicate](#remove) per i dettagli sulla verifica dell&#39;esistenza dei duplicati e sulla loro rimozione.

## Patch

La patch è allegata a questo articolo. Per scaricarlo, scorri verso il basso fino alla fine dell’articolo e fai clic sul nome del file, oppure fai clic sul seguente collegamento:

[Scarica MDVA-10974\_EE\_2.2.3\_COMPOSER\_v2.patch](assets/MDVA-10974_EE_2.2.3_COMPOSER_v2.patch.zip)

### Versioni compatibili di Adobe Commerce:

La patch è stata creata per:

* Adobe Commerce 2.2.3

La patch è compatibile (ma potrebbe non risolvere il problema) anche con le seguenti versioni ed edizioni di Adobe Commerce:

* Adobe Commerce sull’infrastruttura cloud 2.2.1 - 2.2.5
* Adobe Commerce on-premise 2.2.1 - 2.2.2 e 2.2.4 - 2.2.5

## Come applicare il cerotto

Consulta [Come applicare una patch del compositore fornita dall&#39;Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) per istruzioni nella knowledge base di supporto.

## Rimuovi le voci duplicate {#remove}

>[!NOTE]
>
>Assicurati di avere un backup recente prima di qualsiasi manipolazione.

Per individuare le voci duplicate ed eliminarle, eseguire la procedura seguente:

1. Eseguire la query seguente per verificare se le voci duplicate esistono nel database:

   ```SQL
   SELECT entity_id, "catalog_product_entity" AS entity_table FROM catalog_product_entity GROUP BY entity_id, created_in HAVING COUNT(*) > 1    UNION    SELECT entity_id, "catalog_product_entity" AS entity_table FROM catalog_product_entity group by entity_id, updated_in having count(*) > 1    UNION    SELECT rule_id as entity_id, "catalogrule" AS entity_table FROM catalogrule GROUP BY entity_id, created_in HAVING COUNT(*) > 1    UNION    SELECT rule_id as entity_id, "catalogrule" AS entity_table FROM catalogrule GROUP BY entity_id, updated_in HAVING COUNT(*) > 1    UNION    SELECT rule_id as entity_id, "salesrule" AS entity_table FROM salesrule GROUP BY entity_id, created_in HAVING COUNT(*) > 1    UNION    SELECT rule_id as entity_id, "salesrule" AS entity_table FROM salesrule GROUP BY entity_id, updated_in HAVING COUNT(*) > 1    UNION    SELECT page_id as entity_id, "cms_page" AS entity_table FROM cms_page GROUP BY entity_id, created_in HAVING COUNT(*) > 1    UNION    SELECT page_id as entity_id, "cms_page" AS entity_table FROM cms_page GROUP BY entity_id, updated_in HAVING COUNT(*) > 1    UNION    SELECT block_id as entity_id, "cms_block" AS entity_table FROM cms_block GROUP BY entity_id, created_in HAVING COUNT(*) > 1    UNION    SELECT block_id as entity_id, "cms_block" AS entity_table FROM cms_block GROUP BY entity_id, updated_in HAVING COUNT(*) > 1;
   ```

   Se non sono presenti voci duplicate, la risposta sarà vuota e non è necessario eseguire altre operazioni. Se esistono voci duplicate, si otterrà il nome della tabella e `entity_id` dell’entità duplicata, come nell’esempio seguente:

   ![table_results1.png](assets/table_results1.png)

   Considera che in alcune tabelle il nome del campo con ID entità sarà diverso da `entity_id`. Ad esempio, nel `cms_page` tabella, sarebbe `page_id` invece di `entity_id`.

1. Successivamente, è necessario esaminare più da vicino i duplicati e capire quali devono essere rimossi. Utilizza una query simile alla seguente per visualizzare i duplicati. Sostituisci il nome della tabella, il nome dell’ID entità e il valore in base ai risultati ricevuti nel passaggio precedente.

   ```sql
   SELECT row_id, entity_id, created_in, updated_in FROM catalog_product_entity WHERE entity_id = 483 ORDER BY created_in;
   ```

   Verrà visualizzato un elenco di record con più colonne. Esempio:

   ![table_results2.png](assets/table_results2.png)

   Il `created_in` e `updated_in` I valori devono seguire questo schema: `created_in` il valore della riga corrente è uguale al `updated_in` nella riga precedente. Inoltre, il **prima riga** deve contenere created\_in = 1 e il **ultima riga** deve contenere aggiornato\_in = 2147483647. (Se c&#39;è solo 1 riga, devi vedere creato\_in=1 **e** aggiornato\_in=2147483647). Le righe per le quali questo pattern è interrotto devono essere eliminate. Nel nostro esempio, sarebbe la riga con `row_id` =2052 poiché la seconda e la terza riga condividono entrambe lo stesso valore per created_in: 1540837826, che non dovrebbe verificarsi.

1. Elimina il duplicato utilizzando una query simile alla seguente. Sostituisci il nome della tabella, il nome dell’ID entità e il valore in base ai risultati ricevuti nei passaggi precedenti:

   ```sql
   DELETE FROM catalog_product_entity WHERE entity_id = 483 AND row_id = 2052;
   ```

1. Pulisci cache eseguendo:

   ```bash
   bin/magento cache:clean
   ```

   o in Commerce Admin in **Sistema** > **Strumenti** > **Gestione cache**.

## Link utili nella documentazione per gli sviluppatori

* [Applicare patch personalizzate ad Adobe Commerce sull’infrastruttura cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)
* [Visualizzare e gestire i registri per Adobe Commerce sull’infrastruttura cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html))

## File allegati
