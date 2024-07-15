---
title: Errore di elaborazione di OMS (Magenti Order Management System) per Adobe Commerce
description: Questo articolo fornisce una soluzione al problema quando si riceve un errore "getMode()" nella CLI che esegue "bin/magento oms:messages:process" nel sistema di Magento Order Management (OMS) per Adobe Commerce.
exl-id: 83089465-f810-4a3b-bdb6-4720b44f0b49
feature: System
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 0%

---

# Errore di elaborazione di OMS (Magenti Order Management System) per Adobe Commerce

Questo articolo fornisce una soluzione al problema quando si riceve un errore `getMode()` nell&#39;interfaccia CLI che esegue `bin/magento oms:messages:process` nel Magento Order Management (OMS) per Adobe Commerce.

## Prodotti e versioni interessati

Questo errore si verifica quando si utilizza MCOM Connector versione 3.1.1 e 3.2.0. Viene risolto nel connettore MCOM 3.3.0. Non è specifico per una versione MDC o MOM.

## Problema

Quando si esegue il comando seguente nella CLI:

`bin/magento oms:messages:process`

Nell&#39;interfaccia CLI viene visualizzato un messaggio di errore simile al seguente:

```
<project-id>@<project-id>:~$ php bin/magento oms:messages:process

Processing messages...

PHP Fatal error:Uncaught Error: Call to a member function getMode()
on null in /app/<project-id>/vendor/magento/module-inventory-message-bus/Handler/OnAggregateStockUpdatedSubscriber.php:64

Stack trace:

  #0 [internal function]: Magento\InventoryMessageBus\Handler\OnAggregateStockUpdatedSubscriber->onUpdated(Object(Magento\InventoryMessageBus\Model\Event\OnAggregateStockUpdated))

  #1 /app/<project-id>/vendor/magento/module-service-bus/Message/SingleMessageProcessor.php(81):
  call_user_func(Array, Object(Magento\InventoryMessageBus\Model\Event\OnAggregateStockUpdated))

  #2 [internal function]: Magento\ServiceBus\Message\SingleMessageProcessor->Magento\ServiceBus\Message\\{closure}(Array)

  #3 /app/<project-id>/vendor/magento/module-service-bus/Message/SingleMessageProcessor.php(86):
  array_map(Object(Closure), Array)

  #4 /app/<project-id>/vendor/magento/module-service-bus/Message/Processor.php(110):
  Magento\ServiceBus\Message\SingleMessageProcessor->process(Object(Magento\CommonMessageBus\Message\Message))

  #5 /app/t in /app/<project-id>/vendor/magento/module-inventory-message-bus/Handler/OnAggregateStockUpdatedSubscriber.php
  on line 64
```

## Causa

Â
Ciò si verifica quando il connettore tenta di elaborare `magento.inventory.source_management` messaggi. Il connettore tenta di elaborare questi messaggi come se fossero un messaggio `magento.inventory.source_stock_management.update` che richiede un valore di modalità. Poiché nei messaggi `magento.inventory.source_mangement` non è presente alcuna modalità, l&#39;errore si verifica.

## Soluzione

Per risolvere il problema, eseguire l&#39;istruzione SQL seguente nella CLI che elimina tutti i record nella tabella `mcom_api_messages`:

`delete from mcom_api_messages;`

## Lettura correlata

Vedere l&#39;esercitazione sull&#39;installazione del connettore OMS [OMS Docs](https://omsdocs.magento.com/en/integration/connector/setup-tutorial/).
