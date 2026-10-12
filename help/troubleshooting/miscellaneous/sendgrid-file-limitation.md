---
title: Limitazione di [!DNL SendGrid] file per Adobe Commerce Cloud
description: Questo articolo fornisce una soluzione alternativa alla limitazione [!DNL SendGrid] per Adobe Commerce sull'infrastruttura cloud.
feature: Deploy, Marketing Tools
role: Developer, Admin
exl-id: 48629f48-8100-4128-9211-53d947aecd49
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%
---
# Limitazione di [!DNL SendGrid] per Adobe Commerce Cloud

Questo articolo fornisce alcune soluzioni alternative alla limitazione [!DNL SendGrid] per l&#39;infrastruttura Adobe Commerce su cloud.

## Prodotti e versioni interessati

* Adobe Commerce sull&#39;infrastruttura cloud, [tutte le versioni supportate](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)


## Problema

Si tenta di inviare allegati di grandi dimensioni nelle e-mail e vengono visualizzati i seguenti errori di registro:

In `/var/log/mail.log`

```shell
Month Date Time i-xxxxxxxxxxxxxxxxx postfix/sendmail[21408]: fatal: no-reply@xxxxxxxx.com(8080): message file too big
Month Date Time i-xxxxxxxxxxxxxxxxx postfix/sendmail[26434]: fatal: no-reply@xxxxxxxxx.com(8080): message file too big
```

In `/var/log/exception.log`

Produzione:

`/app/<project-id>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

Staging:

`/app/<project-id_stg>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

Staging2:

`/app/<project-id_stg2>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

## Causa

[!DNL SendGrid] ha un limite di sistema di 30 MB per la posta elettronica. Si consiglia di non utilizzare allegati con dimensioni superiori a 10 Mb. Per ulteriori informazioni, vedere [Invio di allegati](https://docs.sendgrid.com/ui/sending-email/attachments-with-digioh) nella documentazione di SendGrid.

## Soluzione alternativa

* Non utilizzare allegati di dimensioni superiori a 6 MB o 10 MB.
* Prendi in considerazione l’utilizzo di un server SMTP remoto nell’istanza di Adobe Commerce. Per i passaggi, consulta [Configurare le comunicazioni e-mail](https://experienceleague.adobe.com/docs/commerce-admin/systems/communications/email-communications.html?lang=it) nella Guida ai sistemi di amministrazione.
* Riconfigura il server in modo che i file possano essere salvati all’interno del modulo, quindi allega il collegamento ai file nelle e-mail.

## Lettura correlata

* [[!DNL SendGrid] servizio e-mail](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/sendgrid.html?lang=it) nella guida all&#39;infrastruttura Commerce on Cloud.
