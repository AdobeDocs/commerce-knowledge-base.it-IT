---
title: È stato aumentato il tempo di esecuzione per gli endpoint web asincroni in blocco dopo la patch di sicurezza APSB25-08
description: Questo articolo fornisce un hotfix per il problema in cui le richieste POST rest/all/async/bulk/V1/products per più di 1000 voci registrano un aumento significativo dei tempi di esecuzione dopo l’applicazione della patch di sicurezza APSB25-08.
feature: Security, Cache, REST, Products, Customers
role: Admin, Developer
source-git-commit: fce7f860b9fddd694b311ffc4acd56a48c06e14b
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# È stato aumentato il tempo di esecuzione per tutti gli endpoint web asincroni in blocco dopo la patch di sicurezza APSB25-08

Questo articolo fornisce un hotfix per tutti gli endpoint web asincroni in blocco come `POST rest/all/async/bulk/V1/products` con più di 1000 voci che stanno avendo tempi di esecuzione significativamente più lunghi dopo l&#39;applicazione della patch di sicurezza APSB25-08.

## Prodotti e versioni interessati

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4, 2.4.4-p1, 2.4.4-p2, 2.4.4-p3, 2.4.4-p4, 2.4.4-p5, 2.4.4-p6, 2.4.4-p7, 2.4.4-p8, 2.4.4-p9, 2.4.4-p10, 2.4.4-p11, 2.4.4-p12

* Adobe Commerce (tutti i metodi di distribuzione) 2.4.5, 2.4.5-p1, 2.4.5-p2, 2.4.5-p3, 2.4.5-p4, 2.4.5-p5, 2.4.5-p6, 2.4.5-p7, 2.4.5-p8, 2.4.5-p9, 2.4.5-p10, 2.4.5-p11

* Adobe Commerce (tutti i metodi di distribuzione) 2.4.6, 2.4.6-p1, 2.4.6-p2, 2.4.6-p3, 2.4.6-p4, 2.4.6-p5, 2.4.6-p6, 2.4.6-p7, 2.4.6-p8, 2.4.6-p9

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7, 2.4.7-p1, 2.4.7-p2, 2.4.7-p3, 2.4.7-p4

* Adobe Commerce (tutti i metodi di implementazione) 2.4.8

## Problema

Dopo l&#39;applicazione della patch di sicurezza APSB25-08, `POST rest/all/async/bulk/V1/products` richieste con più di 1000 voci richiedono molto più tempo per l&#39;esecuzione.

<u>Passaggi da riprodurre</u>:

1. Effettuare una richiesta `POST rest/all/async/bulk/V1/products` con più di 1000 voci (è sufficiente specificare nome, SKU e descrizione).
1. Prendi nota del tempo impiegato per la richiesta.
1. Applica la patch di sicurezza APSB25-08 e ripulisci i dati generati e la cache utilizzando `se:di:co`.
1. Esegui `bin/magento c:f`.
1. Vai alla vetrina per assicurarti che la cache e i file generati siano presenti.
1. Ripeti la richiesta dal passaggio 1.
1. Nota il tempo necessario per la richiesta.
1. Rimuovi la patch di sicurezza APSB25-08, svuota la cache, rigenera il codice e ripeti la richiesta dal passaggio 1 per confermare che il tempo di esecuzione ritorni alla normalità. (Facoltativo)

<u>Risultati previsti</u>:

Il tempo di esecuzione per `async/bulk` richieste è aumentato in modo significativo dopo l&#39;applicazione della patch di sicurezza.

<u>Risultati effettivi</u>:

Il tempo di esecuzione per le richieste `async/bulk` non deve essere aumentato in modo significativo dopo l&#39;applicazione della patch di sicurezza, anche se è previsto un aumento del tempo.

## Soluzione

Per risolvere il problema, applica [AC-14078-2-4x-poser-patch.zip](assets/AC-14078-2-4x-composer-patch.zip).

## Come applicare il cerotto

Decomprimi il file e vedi [Come applicare una patch del compositore fornita da Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html?lang=it) nella Knowledge Base di supporto per le istruzioni.

## Lettura correlata

* [Aggiornamento di sicurezza disponibile per Adobe Commerce - APSB25-08](/help/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-08.md)
