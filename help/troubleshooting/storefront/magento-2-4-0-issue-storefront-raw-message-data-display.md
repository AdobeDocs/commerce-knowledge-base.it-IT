---
title: "Problema Adobe Commerce 2.4.0: visualizzazione dei dati dei messaggi non elaborati in vetrina"
description: Questo articolo fornisce una soluzione al problema quando tutti i messaggi di errore nella vetrina vengono visualizzati con un segno "+" invece di uno spazio. Questa soluzione consente ai messaggi di errore di rimanere leggibili.
exl-id: f44fe434-a320-4e7e-a876-9575921749f3
feature: Storefront
role: Admin
source-git-commit: a1046621259ea49eab74cd6ba3bba550e0c70283
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---

# problema Adobe Commerce 2.4.0: visualizzazione dei dati dei messaggi non elaborati in vetrina

Questo articolo fornisce una soluzione al problema quando tutti i messaggi di errore nella vetrina vengono visualizzati con un segno &quot;+&quot; invece di uno spazio. Questa soluzione consente ai messaggi di errore di rimanere leggibili.

## Prodotti e versioni interessati

* Adobe Commerce sull’infrastruttura cloud 2.4.0
* Adobe Commerce locale 2.4.0.

## Problema

<u>Passaggi da riprodurre:</u>

1. Vai alla pagina **Crea nuovo account** nella vetrina.
1. Crea un nuovo account tramite e-mail registrata. Viene visualizzato il seguente messaggio:

`There+is+already+an+account+with+this+email+address.+If+you+are+sure+that+it+is+your+email+address,+click+here+to+get+your+password+and+access+your+account.`

## Causa

Il problema è causato da un problema PHP 7.4.2 relativo a set\\read cookies. Vedere [PHP BUG \#79174 setcookie() codifica lo spazio come \`+\`, ma $\_COOKIE non li decodifica più](https://bugs.php.net/bug.php?id=79174).

## Soluzione

Per risolvere questo problema, utilizzare un&#39;altra versione di PHP 7.4.x. PHP 7.4.2 non è supportato da Adobe Commerce 2.4.0.

## Letture correlate nella knowledge base di supporto:

* [Problema noto di Commerce 2.4.0: i metodi di pagamento Braintree non vengono visualizzati nel checkout di più indirizzi](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problema noto di Adobe Commerce 2.4.0: l’aggiornamento delle attività del cliente non funziona](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problema noto di Adobe Commerce 2.4.0: l’esportazione delle aliquote fiscali non funziona](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problema noto di Adobe Commerce 2.4.0: il pulsante &quot;Aggiungi selezioni al carrello&quot; non funziona](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
