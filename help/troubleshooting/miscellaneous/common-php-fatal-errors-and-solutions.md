---
title: Errori irreversibili PHP comuni e soluzioni
description: Questo articolo elenca alcuni esempi rapidi di errore irreversibile PHP comuni che puoi trovare quando esamini i registri di Adobe Commerce e le soluzioni per i problemi indicati.
exl-id: 3e42d38f-97bc-4d38-8e36-23b1453f81d9
feature: Support
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---

# Errori irreversibili PHP comuni e soluzioni

Questo articolo elenca alcuni esempi rapidi di errore irreversibile PHP comuni che puoi trovare quando esamini i registri di Adobe Commerce e le soluzioni per i problemi indicati.

## Esempio

*&#39;PHP Errore irreversibile: tempo massimo di esecuzione di 60 secondi superato in....&#39;*

## Soluzione

È possibile aggiornare il tempo massimo di esecuzione impostando un valore `max_execution_time` personalizzato nel file `php.ini` e ridistribuendolo.

Ad esempio:

`max_execution_time = 120`

Consulta l&#39;articolo [Personalizzare le impostazioni php.ini](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/configure/app/php-settings).

## Esempio

*&#39;PHP Errore irreversibile: dimensione di memoria consentita di 792723456 byte esauriti&#39;* (solo un esempio di dimensione in byte).

## Soluzione

Personalizzare le impostazioni di `php.ini`. Consulta questo articolo [Personalizzare le impostazioni php.ini](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/configure/app/php-settings).

## Esempio

*&#39;Avviso PHP: sconosciuto: impossibile aprire il flusso: file o directory non esistente&#39;*

## Soluzione

Assicurarsi di non rimuovere le terminazioni in stile Windows nel file `php.ini`. In Windows, le terminazioni di riga sono terminate con una combinazione di un ritorno a capo (ASCII 0x0d o \r) e una nuova riga (\n), detta anche CR/LF.

## Esempio

Errore irreversibile PHP *: eccezione PDOE non rilevata: SQLSTATE\[HY000\] \[1040\] Troppe connessioni in&#39;*

## Soluzione

Spazio su disco insufficiente nell&#39;ambiente MySQL. Fornire più spazio su disco per l&#39;ambiente MySQL.

## Esempio

Errore irreversibile PHP *: TypeError non rilevato: valore restituito del Magento &#39;*

## Soluzione

Controllare la directory `<root>/tmp` perché è probabilmente piena. Se è pieno, fornisci più spazio nella directory. Questo potrebbe comportare semplicemente lo spostamento di file in un’altra directory o la loro eliminazione.

## Lettura correlata

Nella documentazione per gli sviluppatori:

* [Errori impostazioni PHP](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/troubleshooting/overview)
* [Impostazioni PHP richieste](https://experienceleague.adobe.com/it/docs/commerce-operations/installation-guide/prerequisites/php-settings)
* [Verifica Redis](https://experienceleague.adobe.com/it/docs/commerce-operations/configuration-guide/cache/redis/redis-session#verify-redis-connection)
* [Configura Redis](https://experienceleague.adobe.com/it/docs/commerce-operations/configuration-guide/cache/redis/config-redis)
* [Errore limite memoria PHP](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/troubleshooting/overview)
* [Soluzioni ai problemi comuni - Limite di memoria](https://developer.adobe.com/commerce/testing/guide/unit/command-line/#solutions-to-common-problems)
