---
title: 'Errore cURL 60: certificato SSL scaduto'
description: 'Questo articolo mostra come verificare quando è stata distribuita l’ultima volta un ramo dopo aver ricevuto un errore cURL 60: certificato SSL scaduto nei rami Principale o Integrazione su Adobe Commerce nell’infrastruttura cloud.'
exl-id: 74f1db7e-ee2b-4e27-8fcc-fe462a9e72c3
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---

# Errore cURL 60: certificato SSL scaduto

Questo articolo mostra come verificare quando è stata distribuita l&#39;ultima volta un ramo dopo aver ricevuto un `cURL error 60`: [!DNL SSL certificate] scaduto nei rami [!DNL Master] o [!DNL Integration] in Adobe Commerce sull&#39;infrastruttura cloud.

## Prodotti e versioni interessati

* Adobe Commerce sull&#39;infrastruttura cloud, [tutte le versioni supportate](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Causa

[!DNL SSL certificates] in questi rami sono validi solo per 30 giorni e il ramo potrebbe non essere stato ridistribuito in più di 30 giorni.

L’errore sarà simile al seguente:

```cURL
cURL error 60: SSL certificate problem: certificate has expired
```

## Soluzione

Controlla quando è stata implementata l’ultima volta il ramo. Se supera la soglia di 30 giorni, ridistribuisci il ramo.

Due metodi per verificare quando è stata eseguita l’ultima distribuzione:

* [Metodo 1: utilizzare [!DNL magento-cloud] CLI](#meth2).
* [Metodo 2: aprire  [!DNL Project URL]](#meth3).

Se la distribuzione è stata completata correttamente, [!DNL SSL certificate] verrà automaticamente rinnovato.

Se la distribuzione non riesce e hai bisogno di assistenza per risolverla, [invia un ticket di supporto](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=it#submit-ticket).

### Metodo 1: utilizzare [!DNL magento-cloud] CLI {#meth2}

Esegui questo comando: `magento-cloud activity:list`

### Metodo 2: aprire [!DNL Project URL] {#meth3}

Passare a, ad esempio: `https://demo.magento.cloud/#/projects/<project>/environments/<environment>`, e verificare quando è stata eseguita l&#39;ultima distribuzione.

## Lettura correlata

Nella documentazione per gli sviluppatori:

* [API Cloud Manager: SSLCertificates](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/SSLCertificates)
* [Configurazione rapida: provisioning dei certificati SSL/TLS](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#provision-ssltls-certificates)

Nella nostra knowledge base di supporto:

* [Informazioni sulla scadenza del certificato SSL personalizzato](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/custom-ssl-certificate-expiration-information.html?lang=it)
* [Certificati SSL (TLS) per Adobe Commerce sull&#39;infrastruttura cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/ssl-tls-certificates-for-magento-commerce-cloud-faq.html?lang=it)
