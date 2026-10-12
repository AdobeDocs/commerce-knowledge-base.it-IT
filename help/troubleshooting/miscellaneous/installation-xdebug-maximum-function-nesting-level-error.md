---
title: Errore del livello massimo di nidificazione della funzione xdebug di installazione
description: In questo articolo viene fornita una correzione per l'errore del livello massimo di nidificazione delle funzioni xdebug durante l'installazione.
exl-id: 1f64a9bb-59a7-41df-92a4-890d9d32bcbe
feature: Install
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 0%
---
# Errore del livello massimo di nidificazione della funzione xdebug di installazione

In questo articolo viene fornita una correzione per l&#39;errore del livello massimo di nidificazione delle funzioni xdebug durante l&#39;installazione.

## Dettagli

Durante l’installazione di Adobe Commerce, viene visualizzato un messaggio simile al seguente:

`PHP Fatal error: Maximum function nesting level of '100' reached, aborting! in <path>/ClassLoader.php`

Si consiglia vivamente di NON UTILIZZARE `xdebug` in un ambiente di produzione.

## Soluzione

Si è verificato un problema noto con `xdebug` che può influire sulle installazioni di Adobe Commerce o sull&#39;accesso alla vetrina o all&#39;amministratore Commerce dopo l&#39;installazione.

Per informazioni dettagliate, consulta [Problema noto con xdebug](/help/troubleshooting/miscellaneous/known-issues-that-affect-installation.md) nella knowledge base di supporto.
