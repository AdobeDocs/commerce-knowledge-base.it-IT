---
title: I clienti si disconnettono o perdono il contenuto del carrello nella vetrina Adobe Commerce
description: Questo articolo fornisce una soluzione al problema, in cui i clienti si disconnettono o perdono elementi dal carrello della vetrina, dopo essere stati reindirizzati al negozio di Adobe Commerce dal pagamento o da altri servizi di terze parti (il cookie di sessione "viene perso").
exl-id: 9175570c-b06c-4a65-b8ca-7a12ff266afb
feature: Orders, Page Content, Shopping Cart, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 0%

---

# I clienti si disconnettono o perdono il contenuto del carrello nella vetrina Adobe Commerce

Questo articolo fornisce una soluzione al problema, in cui i clienti si disconnettono o perdono elementi dal carrello sulla vetrina, dopo essere stati reindirizzati al negozio di Adobe Commerce dal pagamento o da altri servizi di terze parti (cookie di sessione &quot;viene perso&quot;).

## Prodotti e versioni interessati

* Adobe Commerce on-premise [tutte le versioni supportate](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)
* Adobe Commerce sull’infrastruttura cloud, [tutte le versioni supportate](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problema

<u>Passaggi da riprodurre:</u>

1. Il cliente aggiunge prodotti al carrello nella vetrina e procede al pagamento.
1. Il cliente viene reindirizzato al sito di terze parti per il pagamento/la spedizione o altre informazioni/servizi.
1. Il cliente viene reindirizzato al negozio.

<u>Risultato effettivo:</u>

Il cliente viene reindirizzato al carrello vuoto o a una pagina vuota.

<u>Risultato previsto:</u>

Cliente reindirizzato a una pagina di pagamento riuscita (o altra pagina di successo), senza perdere i dati di pagamento e l&#39;avanzamento.

## Causa

L’attributo per cookie SameSite è impostato su *Lax* o non specificato (considerato impostato su *Lax* ). Avendo `SameSite` = *Lax* disabilita il trasferimento di un cookie a URL esterni tramite `POST` richieste.

## Soluzione

Per risolvere il problema, contatta il provider di servizi di terze parti e richiedi ai relativi sviluppatori di aggiornare le integrazioni per configurare i parametri dei cookie.

## Lettura correlata

[Aggiornamento SameSite di Chrome](https://www.chromestatus.com/feature/5088147346030592)
