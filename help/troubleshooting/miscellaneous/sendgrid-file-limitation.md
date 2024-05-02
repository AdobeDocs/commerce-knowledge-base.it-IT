---
title: '[!DNL SendGrid] limitazione dei file per Adobe Commerce Cloud'
description: Questo articolo fornisce una soluzione alternativa alla  [!DNL SendGrid] limitazione per Adobe Commerce sull’infrastruttura cloud.
feature: Deploy, Marketing Tools
role: Developer, Admin
exl-id: 48629f48-8100-4128-9211-53d947aecd49
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---

# [!DNL SendGrid] limitazione per Adobe Commerce Cloud

Questo articolo fornisce alcune soluzioni per [!DNL SendGrid] limitazione per l’infrastruttura Adobe Commerce on Cloud.

## Prodotti e versioni interessati

* Adobe Commerce sull’infrastruttura cloud, [tutte le versioni supportate](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)


## Problema

Si tenta di inviare allegati di grandi dimensioni nelle e-mail e vengono visualizzati i seguenti errori di registro:

In entrata `/var/log/mail.log`

```shell
Month Date Time i-xxxxxxxxxxxxxxxxx postfix/sendmail[21408]: fatal: no-reply@xxxxxxxx.com(8080): message file too big
Month Date Time i-xxxxxxxxxxxxxxxxx postfix/sendmail[26434]: fatal: no-reply@xxxxxxxxx.com(8080): message file too big
```

In entrata `/var/log/exception.log`

Produzione:

`/app/<project-id>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

Staging:

`/app/<project-id_stg>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

Staging2:

`/app/<project-id_stg2>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

## Causa

[!DNL SendGrid] ha un limite di sistema di 30 Mb per le e-mail. Si consiglia di non utilizzare allegati con dimensioni superiori a 10 Mb. Consulta [Invio di allegati](https://docs.sendgrid.com/ui/sending-email/attachments-with-digioh) nella documentazione di SendGrid per ulteriori informazioni.

## Soluzione alternativa

* Non utilizzare allegati di dimensioni superiori a 6 MB o 10 MB.
* Prendi in considerazione l’utilizzo di un server SMTP remoto nell’istanza di Adobe Commerce. Per i passaggi, consulta [Configurare le comunicazioni e-mail](https://experienceleague.adobe.com/docs/commerce-admin/systems/communications/email-communications.html) nella nostra Guida ai sistemi di amministrazione.
* Riconfigura il server in modo che i file possano essere salvati all’interno del modulo, quindi allega il collegamento ai file nelle e-mail.

## Lettura correlata

* [[!DNL SendGrid] servizio e-mail](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/sendgrid.html) nella Guida all’infrastruttura Commerce on Cloud.
