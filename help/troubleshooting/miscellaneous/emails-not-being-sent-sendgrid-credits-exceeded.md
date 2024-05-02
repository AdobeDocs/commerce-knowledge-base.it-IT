---
title: Messaggi e-mail non inviati quando in Adobe Commerce sono stati superati i crediti SendGrid
description: Questo articolo fornisce una soluzione quando le e-mail non vengono inviate perché è stato superato il limite di crediti SendGrid in Adobe Commerce.
exl-id: 43438890-665b-4408-8034-e61de8fbbd8b
feature: Communications, Orders
role: Developer
source-git-commit: e04bb0b37e795cae3380e1110e6db95be12036b0
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Messaggi e-mail non inviati quando in Adobe Commerce sono stati superati i crediti SendGrid

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud 2.3.0 - 2.3.7-p1, 2.4.0 - 2.4.3

## Problema

I crediti SendGrid si riferiscono al numero di e-mail consentite che possono essere inviate. È possibile inviare solo 12.000 e-mail al mese dai rami di integrazione e staging. I crediti vengono rinnovati all’inizio del mese, quindi se si esaurisce il credito, si dovrà attendere il rinnovo.

Non ci sono limiti rigidi al numero di e-mail che possono essere inviate in Produzione, purché la reputazione del mittente sia superiore al 95%. La reputazione è influenzata dal numero di e-mail non recapitate/rifiutate e dal fatto che i registri di posta indesiderata basati su DNS abbiano contrassegnato il dominio come potenziale origine di posta indesiderata. In Produzione, vengono allocate in totale 12.000 e-mail al giorno, ma tale numero può essere esteso in base alla media del numero di e-mail inviate nei cinque giorni precedenti.

## Come verificare se i crediti sono stati superati:

Architettura del piano Pro di Adobe Commerce su infrastruttura cloud: controlla `/var/log/mail.log` - potresti visualizzare un messaggio come questo:

`May 28 21:13:00 <i-node> postfix/error[21335]: BC7941A2BBF: to=<to@email.com>, relay=none, delay=4642, delays=4642/0.56/0/0.03, dsn=4.0.0, status=deferred (delivery temporarily suspended: SASL authentication failed; server smtp.sendgrid.net[ip address] said: 451 Authentication failed: Maximum credits exceeded).`

## Causa

Il numero di e-mail consentite che possono essere inviate è limitato.

## Soluzione

* Se visualizzi questo messaggio nell&#39;ambiente di produzione, [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) e inviare il messaggio di cui sopra e richiedere l’aumento dei crediti.
* Se non visualizzi questo messaggio o ti trovi su Adobe Commerce on cloud infrastructure Starter plan architecture, [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) e di menzionare che `mail.log` non indica che i crediti sono stati superati.

## Lettura correlata

* [InviaGriglia](https://devdocs.magento.com/cloud/project/sendgrid.html) nella documentazione per gli sviluppatori.
