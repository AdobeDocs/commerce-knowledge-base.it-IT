---
title: Errore del livello massimo di nidificazione della funzione xdebug di installazione
description: In questo articolo viene fornita una correzione per l'errore del livello massimo di nidificazione delle funzioni xdebug durante l'installazione.
exl-id: 1f64a9bb-59a7-41df-92a4-890d9d32bcbe
feature: Install
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
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
