---
title: Coupon monouso viene utilizzato più volte, Adobe Commerce
description: Questo articolo fornisce una soluzione per il problema quando i coupon della regola di prezzo del carrello non funzionano correttamente. Gli esercenti impostano un coupon per singolo utilizzo e i clienti possono utilizzarlo più volte.
exl-id: 9c81de40-65a3-422d-9053-3c894b863a0a
feature: Orders
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 0%
---
# Coupon monouso viene utilizzato più volte, Adobe Commerce

Questo articolo fornisce una soluzione per il problema quando i coupon della regola di prezzo del carrello non funzionano correttamente. Gli esercenti impostano un coupon per singolo utilizzo e i clienti possono utilizzarlo più volte.


## Prodotti e versioni interessati

Adobe Commerce (tutti i metodi di implementazione) 2.4.3 e versioni successive

## Problema

Gli esercenti impostano un coupon per singolo utilizzo e i clienti possono utilizzarlo più volte.

<u>Passaggi da riprodurre</u>:

1. Crea un coupon e configuralo per un singolo utilizzo.
1. Procedi con il pagamento.
1. Utilizza il coupon appena creato.
1. Procedi di nuovo al pagamento e utilizza lo stesso coupon.

<u>Risultato previsto</u>:

Il coupon può essere utilizzato una sola volta. Viene visualizzato un messaggio: *Il codice coupon &quot;COUPON_NAME&quot; non è valido*.

<u>Risultato effettivo</u>:

Il coupon può essere utilizzato più volte.


## Causa

I commercianti non dispongono di `sales.rule.update.coupon.usage` consumer configurato e in esecuzione che provocano un comportamento non corretto.

## Soluzione

Aggiungere il consumer `sales.rule.update.coupon.usage` al file `app/etc/env.php`.

```php
...
    'cron_consumers_runner' =>
    array [
        'cron_run' => true,
        'max_messages' => 20000,
        'consumers' =>
        array [
            'sales.rule.update.coupon.usage'
        ]
    ],
...
```

Per i passaggi dettagliati, consulta [Gestione delle code di messaggi > Configurazione](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/message-queues/manage-message-queues#configuration) nella documentazione per gli sviluppatori.

## Lettura correlata

[Panoramica delle code di messaggi](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/message-queues/message-queue-framework) nella documentazione per gli sviluppatori.
