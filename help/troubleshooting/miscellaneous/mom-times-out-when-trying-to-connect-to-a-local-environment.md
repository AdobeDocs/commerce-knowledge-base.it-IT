---
title: Timeout di Magenti Order Management System (OMS) per Adobe Commerce
description: Questo articolo fornisce una soluzione per il problema in cui il Magento Order Management di sistema (OMS) per Adobe Commerce non può registrare il microservizio installato localmente con MOM utilizzando ngrok, perché MOM si interrompe quando tenta di richiamare.
exl-id: 19149d8c-ea24-46fb-8815-9f637afe46ca
feature: System
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---

# Timeout di Magenti Order Management System (OMS) per Adobe Commerce

Questo articolo fornisce una soluzione per il problema in cui il Magento Order Management di sistema (OMS) per Adobe Commerce non può registrare il microservizio installato localmente con MOM utilizzando ngrok, perché MOM si interrompe quando tenta di richiamare.

## Prodotti e versioni interessati

* Adobe Commerce 2.3.1
* OMS
* ngrok

>[!WARNING]
>
>Esclusione di responsabilità: Adobe Commerce non consiglia o non approva alcuno strumento particolare per la creazione di tunnel. I precedenti sono solo suggerimenti. Per ulteriori informazioni, consulta la [documentazione ngrok](https://ngrok.com/docs).

## Problema

<u>Passaggi da riprodurre</u>

1. Installa Adobe Commerce nell’ambiente locale.
1. Imposta ngrok per creare un tunnel per esporre il server locale.
1. Provare a [connettersi a OMS](https://commerce-docs.github.io/oms-documentation-archive/integration/connector/setup-tutorial/).

<u>Risultato previsto</u>

Connessione stabilita correttamente.

<u>Risultato effettivo</u>

Sembra che MCOM abbia un timeout quando si tenta di richiamare all’URL non gestito.

## Causa

Uno dei possibili motivi del timeout è che i server sono geograficamente troppo lontani e la connessione richiede troppo tempo.

## Soluzione

Aggiungi un parametro che specifica la tua regione all’avvio di ngrok. Come segue:

```bash
./ngrok http 80 -region eu
```

L&#39;area predefinita è Stati Uniti. Vedi [tutti i valori possibili](https://ngrok.com/docs#config_region).
