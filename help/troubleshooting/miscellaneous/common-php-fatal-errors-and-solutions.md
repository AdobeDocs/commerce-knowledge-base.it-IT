---
title: Errori irreversibili PHP comuni e soluzioni
description: Questo articolo elenca alcuni esempi rapidi di errore irreversibile PHP comuni che puoi trovare quando esamini i registri di Adobe Commerce e le soluzioni per i problemi indicati.
exl-id: 3e42d38f-97bc-4d38-8e36-23b1453f81d9
feature: Support
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: a59f76dc-e003-5617-951e-dffa5bd3de81
    internal-label: Support
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '381'
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

*&#39;PHP Errore irreversibile: TypeError non rilevato: valore restituito di Magento&#39;*

## Soluzione

Controllare la directory `<root>/tmp` perché è probabilmente piena. Se è pieno, fornisci più spazio nella directory. Questo potrebbe comportare semplicemente lo spostamento di file in un’altra directory o la loro eliminazione.

## Lettura correlata

Nella documentazione per gli sviluppatori:

* [Errori impostazioni PHP](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/troubleshooting/overview)
* [Impostazioni PHP richieste](https://experienceleague.adobe.com/it/docs/commerce-operations/installation-guide/prerequisites/php-settings)
* [Verifica Redis](https://experienceleague.adobe.com/it/docs/commerce-operations/configuration-guide/cache/redis/redis-session#verify-redis-connection)
* [Configurare Redis](https://experienceleague.adobe.com/it/docs/commerce-operations/configuration-guide/cache/redis/config-redis)
* [Errore limite memoria PHP](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/troubleshooting/overview)
* [Soluzioni ai problemi più comuni - Limite di memoria](https://developer.adobe.com/commerce/testing/guide/unit/command-line#solutions-to-common-problems)
