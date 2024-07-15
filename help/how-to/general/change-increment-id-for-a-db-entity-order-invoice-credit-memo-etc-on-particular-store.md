---
title: Modifica ID incremento per un'entità DB (ordine, fattura, nota di accredito, ecc.) in un particolare negozio
description: Questo articolo illustra come modificare l'ID incremento per un'entità database di Adobe Commerce (DB) (ordine, fattura, nota di accredito, ecc.) in un particolare archivio Adobe Commerce utilizzando l’istruzione SQL "ALTER TABLE".
exl-id: 3704dd97-3639-44dc-9b8b-cf09f0c04e6c
feature: Invoices
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# Modifica ID incremento per un&#39;entità DB (ordine, fattura, nota di accredito, ecc.) in un particolare negozio

Questo articolo illustra come modificare l&#39;ID incremento per un&#39;entità database di Adobe Commerce (DB) (ordine, fattura, nota di accredito, ecc.) in un particolare archivio Adobe Commerce utilizzando l&#39;istruzione SQL `ALTER TABLE`.

## Versioni interessate

* Adobe Commerce on-premise: 2.x.x
* Adobe Commerce sull’infrastruttura cloud: 2.x.x
* MySQL: qualsiasi [versione supportata](https://devdocs.magento.com/guides/v2.2/install-gde/system-requirements-tech.html#database)

## Quando è necessario modificare l’ID incremento (casi)

Potrebbe essere necessario modificare l&#39;ID incremento per le nuove entità DB nei seguenti casi:

* Dopo il ripristino di un backup rigido su un sito live
* Alcuni record degli ordini sono stati persi, ma i loro ID sono già utilizzati dai gateway di pagamento (come PayPal) per il tuo account esercente corrente. In questo caso, i gateway di pagamento interrompono l&#39;elaborazione di nuovi ordini con lo stesso ID, restituendo l&#39;errore &quot;ID fattura duplicato&quot;

>[!NOTE]
>
>Puoi anche risolvere il problema del gateway di pagamento per PayPal consentendo più pagamenti per ID fattura nelle Preferenze di ricezione pagamento di PayPal. Vedi [Richiesta rifiutata gateway PayPal - problema fattura duplicata](/help/troubleshooting/payments/paypal-gateway-rejected-request-duplicate-invoice-issue.md) nella knowledge base del supporto.

## Passaggi preliminari

1. Trova archivi ed entità per i quali modificare il nuovo ID incremento.
1. [Connetti](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/mysql_remote.html) al database MySQL. Per Adobe Commerce su infrastruttura cloud, devi prima [SSH nell&#39;ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Controllare il valore corrente di auto\_increment per la tabella di sequenza entità utilizzando la seguente query:

```sql
SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
```

### Esempio

Se stai controllando un incremento automatico per un ordine nell&#39;archivio con *ID=1*, il nome della tabella sarà:

```sql
'sequence_order_1'
```

Se il valore della colonna `auto_increment` è *1234*, il *ID \#100001234* verrà inserito nell&#39;ordine successivo con *ID=1*.

### Documentazione correlata

* [Configurare una connessione remota al database MySQL](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/mysql_remote.html) nella documentazione per gli sviluppatori.

## Aggiorna entità per modificare l&#39;ID incremento

Aggiorna l’entità utilizzando la seguente query:

```sql
ALTER TABLE sequence_{entity_type}_{store_id} AUTO_INCREMENT = {new_increment_value};
```

>[!WARNING]
>
>Importante: il nuovo valore di incremento deve essere maggiore di quello corrente, non minore.

### Esempio

Dopo l’esecuzione della seguente query:

```sql
ALTER TABLE sequence_order_1 AUTO_INCREMENT = 2000;
```

il *ID \#100002000* verrà emesso per il prossimo ordine con *ID=1*.

## Passaggi aggiuntivi consigliati per l’ambiente di produzione (Cloud)

Prima di eseguire la query `ALTER TABLE` nell&#39;ambiente di produzione di Adobe Commerce sull&#39;infrastruttura cloud, si consiglia vivamente di eseguire i passaggi seguenti:

* Test dell&#39;intera procedura di modifica dell&#39;ID incremento nell&#39;ambiente di staging
* [Crea](/help/how-to/general/create-database-dump-on-cloud.md) un backup del database per ripristinare il database di produzione in caso di errore

## Documentazione correlata

* [Crea un dump del database nel cloud](/help/how-to/general/create-database-dump-on-cloud.md) nella knowledge base di supporto.
* [SSH nell&#39;ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) nella documentazione per gli sviluppatori.
