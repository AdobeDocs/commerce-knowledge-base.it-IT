---
title: Il database contiene più righe per la stessa entità
description: Questo articolo fornisce una soluzione al problema relativo alla presenza di più righe per lo stesso ID entità nel database.
feature: Catalog Management, Categories, Services, Storefront
role: Developer
exl-id: 09d5c321-9c45-4041-b6f6-831efca0977e
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# Più righe nel database per la stessa entità

Questo articolo fornisce una soluzione al problema relativo alla presenza di più righe per lo stesso ID entità nel database.

## Prodotti e versioni interessati:

* Adobe Commerce (tutte le versioni)

## Problema

Nel database sono presenti più righe per lo stesso ID entità.

Ad esempio, dopo aver ricevuto un elenco di record con ID entità duplicati quando esegui questa query:

```
SELECT * FROM $entityTable WHERE $column = <$entityID> ORDER BY created_in;
```

Dove `$entityID = ID` di categoria/prodotto/regola prezzo carrello/regola prezzo catalogo/pagina CMS.

| Entità | $entityTable | $column |
|------------------|-----------------------------------|------------------|
| Categoria/Prodotto | catalog_category_entity/catalog_product_entity | entity_id |
| Regola prezzo carrello/Regola prezzo catalogo | salesrule/catalogrule | rule_id |
| Pagina CMS | cms_page | page_id |

## Causa

Questo è il comportamento previsto. Le più righe vengono create dalla funzionalità di gestione temporanea del contenuto:

* Se specifichi una data di inizio senza una data di fine, ci saranno almeno due righe con lo stesso ID entità/regola/pagina. Una riga indica lo stato originale dell&#39;entità (la riga in cui `created_in=1`) e una riga indica la *fine dell&#39;aggiornamento pianificato*.

* Se specifichi una data di inizio con una data di fine, ci saranno almeno tre righe con lo stesso ID entità/regola/pagina. Una riga indica lo stato originale dell&#39;entità (la riga in cui `created_in=1`), una riga indica l&#39;*Inizio dell&#39;aggiornamento pianificato* e una riga indica la *Fine dell&#39;aggiornamento pianificato*.

Ad esempio, in questa query:

```
SELECT row_id, entity_id, created_in, updated_in FROM catalog_product_entity WHERE entity_id = 483 ORDER BY created_in;
```

![righe_multiple_in_database.png](assets/multiple_rows_in_database.png)

* I valori `created_in` e `updated_in` devono seguire questo schema: il valore `created_in` della riga corrente è uguale al valore `updated_in` della riga precedente. Inoltre, la prima riga deve contenere `created_in = 1` e l&#39;ultima riga `updated_in = 2147483647`. Se è presente una sola riga, è necessario visualizzare `created_in=1` e `updated_in=2147483647`.

### Perché la seconda voce del database (e tutte quelle successive) viene visualizzata nel database per la stessa entità?

* Il secondo record del database (ed eventualmente i successivi) per l&#39;entità interessata indica che sono stati pianificati aggiornamenti di gestione temporanea del contenuto tramite il modulo `Magento_Staging`, che crea un record aggiuntivo per un&#39;entità nelle rispettive tabelle.

Un problema si verifica solo se i record hanno gli stessi valori per le colonne `created_in` o `updated_in`.

## Soluzione

Questo è il comportamento previsto e darà luogo a problemi solo in presenza di discrepanze tra le righe.

## Lettura correlata

* [Le modifiche alle categorie non vengono salvate](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/changes-to-categories-are-not-being-saved.html) nella Knowledge Base di supporto
* [Voci duplicate nella tabella catalogrule dopo la modifica della data di fine di un aggiornamento della pianificazione](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/duplicate-entries-in-the-catalogrule-table-after-editing-the-end-date-of-a-schedule-update.html) nella Knowledge Base di supporto
* [Best practice per la modifica delle tabelle del database](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) nel playbook di implementazione di Commerce
