---
title: Modifica l'ID incremento per un'entità DB (ordine, fattura, nota di accredito, ecc.) in un particolare archivio
description: Questo articolo illustra come modificare l’ID incremento di un’entità database (DB) di Adobe Commerce (ordine, fattura, nota di accredito, ecc.) in un particolare archivio Adobe Commerce utilizzando l’istruzione SQL "ALTER TABLE".
exl-id: 3704dd97-3639-44dc-9b8b-cf09f0c04e6c
feature: Invoices
source-git-commit: e33d0bf6c857d0d54ec1373db79910d78296b054
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 0%

---

# Modifica l&#39;ID incremento per un&#39;entità DB (ordine, fattura, nota di accredito, ecc.) in un particolare archivio

In questo articolo viene illustrato come modificare l&#39;ID incremento per un&#39;entità database (DB) di Adobe Commerce (ordine, fattura, nota di accredito, ecc.) in un particolare archivio Adobe Commerce utilizzando l&#39;istruzione SQL `ALTER TABLE`.

>[!NOTE]
>
>In questo articolo viene descritto solo come modificare il valore numerico iniziale dell&#39;ID incremento per ordini, fatture, note di accredito e così via.
>
>Non descrive come modificare il formato dell’ID di incremento o aggiungere prefissi/suffissi personalizzati (ad esempio, 10000001 a ORDER-10000001, MYSTORE-10000001, 2A10000001 ecc.)
>
>Per personalizzare il formato, è necessario un’estensione personalizzata o un lavoro di sviluppo.

## Versioni interessate

* Adobe Commerce on-premise: 2.x.x
* Adobe Commerce sull’infrastruttura cloud: 2.x.x
* MySQL: qualsiasi [versione supportata](https://experienceleague.adobe.com/it/docs/commerce-operations/installation-guide/system-requirements)

## Quando è necessario modificare l’ID incremento (casi)

Potrebbe essere necessario modificare l&#39;ID incremento per le nuove entità DB nei seguenti casi:

* Dopo il ripristino di un backup rigido su un sito live
* Alcuni record degli ordini sono stati persi, ma i loro ID sono già utilizzati dai gateway di pagamento (come PayPal) per il tuo account esercente corrente. In questo caso, i gateway di pagamento interrompono l&#39;elaborazione di nuovi ordini con lo stesso ID, restituendo l&#39;errore &quot;ID fattura duplicato&quot;

>[!NOTE]
>
>Puoi anche risolvere il problema del gateway di pagamento per PayPal consentendo più pagamenti per ID fattura nelle Preferenze di ricezione pagamento di PayPal. Vedi [Richiesta rifiutata gateway PayPal - problema fattura duplicata](https://experienceleague.adobe.com/it/docs/experience-cloud-kcs/kbarticles/ka-26838) nella knowledge base del supporto.

## Passaggi preliminari

1. Trova archivi ed entità per i quali modificare il nuovo ID incremento.
1. [Connetti](https://experienceleague.adobe.com/it/docs/commerce-operations/installation-guide/prerequisites/database-server/mysql-remote) al database MySQL. Per Adobe Commerce su infrastruttura cloud, devi prima [SSH nell&#39;ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=it).
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

* [Configurare una connessione remota al database MySQL](https://experienceleague.adobe.com/it/docs/commerce-operations/installation-guide/prerequisites/database-server/mysql-remote) nella documentazione per gli sviluppatori.

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

* [Crea un dump del database nel cloud](/help/how-to/general/create-database-dump-on-cloud.md) nella knowledge base di supporto
* [SSH nell&#39;ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=it) nella documentazione per gli sviluppatori
* [Best practice per la modifica delle tabelle del database](https://experienceleague.adobe.com/it/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) nel playbook di implementazione di Commerce
