---
title: "Errore di distribuzione: SQLSTATE[HY000]"
description: Questo articolo fornisce una soluzione per il problema che causa l'errore SQLSTATE[HY000].
exl-id: c6da6275-9327-4a5c-99ed-93a53952ba42
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 0%

---

# Errore di distribuzione: SQLSTATE[HY000]

Questo articolo fornisce una soluzione per il problema in cui la distribuzione non riesce a causa di SQLSTATE[HY000] errore.

## Prodotti e versioni interessati

* Adobe Commerce [tutti i metodi di distribuzione](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problema

Errore SQLSTATE durante la distribuzione.

```sql
Updating modules:
SQLSTATE[HY000]: General error: 23 Out of resources when opening file '/tmp/#sql_565c_0.MAD' (Errcode: 24 "Too many open files"),
```

## Causa

Cron in esecuzione durante la distribuzione.

## Soluzione

Per risolvere il problema, interrompere l&#39;esecuzione di cron aprendo la riga di comando ed eseguendo il comando seguente:
`./vendor/bin/ece-tools cron:disable`.
