---
title: Errori irreversibili PHP comuni e soluzioni
description: Questo articolo elenca alcuni esempi rapidi di errore irreversibile PHP comuni che puoi trovare quando esamini i registri di Adobe Commerce e le soluzioni per i problemi indicati.
exl-id: 3e42d38f-97bc-4d38-8e36-23b1453f81d9
feature: Support
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---

# Errori irreversibili PHP comuni e soluzioni

Questo articolo elenca alcuni esempi rapidi di errore irreversibile PHP comuni che puoi trovare quando esamini i registri di Adobe Commerce e le soluzioni per i problemi indicati.

## Esempio

*&quot;Errore irreversibile PHP: tempo massimo di esecuzione di 60 secondi superato in....&quot;*

## Soluzione

È possibile aggiornare il tempo massimo di esecuzione impostando un `max_execution_time` valore nel tuo `php.ini` e la ridistribuzione.

Ad esempio:

`max_execution_time = 120`

Consulta la [Personalizzare le impostazioni di php.ini](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html) articolo.

## Esempio

*&quot;Errore irreversibile PHP: memoria consentita di 792723456 byte esaurita&quot;* Questo è solo un esempio di dimensione in byte.

## Soluzione

Personalizza `php.ini` impostazioni. Consulta questo [Personalizzare le impostazioni di php.ini](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html) articolo.

## Esempio

*&quot;Avviso PHP: sconosciuto: impossibile aprire il flusso: file o directory non esistente&quot;*

## Soluzione

Assicurati di non rimuovere le terminazioni in stile Windows nel `php.ini` file. In Windows, le terminazioni di riga sono terminate con una combinazione di un ritorno a capo (ASCII 0x0d o \r) e una nuova riga (\n), detta anche CR/LF.

## Esempio

*&quot;Errore irreversibile PHP: eccezione PDOE non rilevata: SQLSTATE\[HY000\] \[1040\] Troppe connessioni in&quot;*

## Soluzione

Spazio su disco insufficiente nell&#39;ambiente MySQL. Fornire più spazio su disco per l&#39;ambiente MySQL.

## Esempio

*&quot;Errore irreversibile PHP: TypeError non rilevato: valore restituito di Magento&quot;*

## Soluzione

Controlla la `<root>/tmp` perché è probabilmente pieno. Se è pieno, fornisci più spazio nella directory. Questo potrebbe comportare semplicemente lo spostamento di file in un’altra directory o la loro eliminazione.

## Lettura correlata

Nella documentazione per gli sviluppatori:

* [Errori impostazioni PHP](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/php/tshoot_php-set.html)
* [Impostazioni PHP richieste](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html)
* [Verifica Redis](https://devdocs.magento.com/guides/v2.3/config-guide/redis/redis-session.html#redis-verify)
* [Configurare Redis](https://devdocs.magento.com/guides/v2.3/config-guide/redis/config-redis.html)
* [Errore limite memoria PHP](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/php/tshoot_php-set.html#trouble-php-memory)
* [Soluzioni ai problemi più comuni - Limite di memoria](https://devdocs.magento.com/guides/v2.3/test/unit/unit_test_execution_cli.html#solutions-to-common-problems)
