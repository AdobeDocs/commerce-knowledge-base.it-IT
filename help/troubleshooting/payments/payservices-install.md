---
title: Risolvere i problemi relativi all'installazione di Payment Services
description: In questo articolo vengono illustrati gli errori che possono verificarsi durante l'installazione di Servizi di pagamento e vengono fornite soluzioni per correggere tali errori in modo da poter completare l'installazione.
exl-id: 0aef7482-8834-400e-85b9-d3d3eb0ab76e
feature: Install, Orders, Payments, Saas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# Risolvere i problemi relativi all&#39;installazione di Payment Services

In questo articolo vengono illustrati gli errori che possono verificarsi durante l&#39;installazione di Servizi di pagamento e vengono fornite soluzioni per correggere tali errori in modo da poter completare l&#39;installazione.

## Prodotti e versioni interessati

* [Payment Services](https://marketplace.magento.com/magento-payment-services.html) è ora compatibile con Adobe Commerce versioni da 2.4.0 a 2.4.4.

## Problema - Chiavi del compositore non corrette

Durante l&#39;installazione dell&#39;estensione Payment Services, è possibile che venga visualizzato un messaggio di errore in cui viene indicato che durante l&#39;installazione sono state utilizzate chiavi di composizione non corrette.

<u>Passaggi da riprodurre</u>:

1. Tentativo di [installare Payment Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html).
1. Vedi il seguente errore:

   *Impossibile trovare una versione corrispondente del pacchetto magento/servizi di pagamento. Verificare che l&#39;ortografia del pacchetto, il vincolo di versione e la disponibilità del pacchetto siano stabili in modo da corrispondere alla stabilità minima (stabile).*

<u>Risultato previsto</u>:

Segui queste [istruzioni di installazione](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html) nella documentazione per gli sviluppatori per installare correttamente Payment Services.

<u>Risultato effettivo</u>:

Durante l&#39;installazione viene visualizzato un messaggio di errore che indica che non sono state utilizzate le chiavi di composizione corrette durante l&#39;installazione.

### Causa

Sono state utilizzate chiavi di composizione errate durante l&#39;installazione.

### Soluzione

Verifica che [le chiavi del Compositore siano collegate all&#39;ID Magento](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html#incorrect-composer-keys) utilizzato durante la registrazione a Payment Services.

## Problema: utilizzo dello stesso spazio dei dati in più istanze

Esecuzione di una configurazione di più ambienti con Payment Services su ciascuno di essi.

### Soluzione

È possibile utilizzare la stessa chiave API in più istanze, ma ogni istanza deve utilizzare il proprio spazio di dati SaaS.

Quando crei un progetto SaaS, Commerce genera uno o più spazi dati SaaS a seconda della licenza Commerce:

* Adobe Commerce: uno spazio dati di produzione; due spazi dati di test
* Magento Open Source: uno spazio dati di produzione; nessuno spazio dati di prova

Segui le istruzioni contenute in [Chiave API Commerce e chiave privata](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#obtain-api-credentials) per configurare correttamente l&#39;estensione Payment Services.

## Problema - Memoria insufficiente per PHP

Durante l&#39;installazione dell&#39;estensione Payment Services, è possibile che venga visualizzato un messaggio di errore che indica che non si dispone di memoria sufficiente per PHP.

<u>Passaggi da riprodurre</u>:

1. Tentativo di [installare Payment Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html).
1. Vedi il seguente errore, o simile:

   *Errore irreversibile: dimensione di memoria consentita di 2146435072 byte esauriti (tentativo di allocare 4096 byte) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php alla riga 52*

<u>Risultato previsto</u>:

Segui queste [istruzioni di installazione](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html) nella documentazione per gli sviluppatori per installare correttamente Payment Services.

<u>Risultato effettivo</u>:

Durante l&#39;installazione viene visualizzato un messaggio di errore che indica che non si dispone di memoria sufficiente per PHP.

### Causa

Il limite per PHP nell’ambiente non è impostato su una soglia sufficientemente alta.

### Soluzione

[Aumentare il limite di memoria per PHP](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html#not-enough-memory-for-php) nell&#39;ambiente in `php.ini`.
