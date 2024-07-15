---
title: "[!DNL Fastly] domande frequenti sull'abilitazione cloaking dell'origine"
description: In questa domanda frequente vengono illustrate le domande comuni sull'abilitazione del cloaking  [!DNL Fastly]  di origine in Adobe Commerce (completamente implementato a partire dal 2021).
exl-id: d608abe7-7d64-44ce-bea1-34b201c29113
source-git-commit: 1021a1ab81481f92e850bd49330f1742fe9a21f2
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# Domande frequenti sull&#39;abilitazione cloaking dell&#39;origine [!DNL Fastly]

In questa domanda frequente vengono illustrate le domande comuni sull&#39;abilitazione del cloaking di origine [!DNL Fastly] in Adobe Commerce (completamente implementato dal 2021).

## Che cos&#39;è il cloaking dell&#39;origine [!DNL Fastly]?

Il cloaking dell&#39;origine è una funzione di sicurezza che consente ad Adobe Commerce sull&#39;infrastruttura cloud di bloccare qualsiasi traffico [!DNL non-Fastly] (per evitare attacchi DDoS, passare all&#39;infrastruttura cloud (origine)).

## Quali sono i vantaggi del cloaking dell’origine?

Il cloaking dell&#39;origine è progettato per evitare che il traffico ignori [!DNL Fastly Web Application Firewall] (WAF) e lo instradi attraverso il flusso rigorosamente definito di **[!DNL Fastly]** > **Load Balancer** > **Istanze**. Con questa implementazione, tutto il traffico sarà garantito attraverso il WAF [!DNL Fastly] e il WAF interno integrato nel load balancer.

## Perché si sta verificando l’abilitazione del cloaking dell’origine?

Questa funzione è stata originariamente creata per avvantaggiare Adobe Commerce sull’infrastruttura cloud.

## Devo richiedere l’abilitazione del cloaking dell’origine per il mio progetto?

No. Questa funzione avrebbe dovuto essere già implementata in tutti i progetti cloud e, per impostazione predefinita, per tutti i progetti il cui provisioning è stato eseguito dal 2021, questa funzione sarebbe stata abilitata.

## Il cloaking dell&#39;origine cambia l&#39;indirizzo IP in uscita?

No, non è così.

## Il cloaking dell’origine influisce sull’API REST?

[!DNL Fastly] non memorizza nella cache le chiamate API, pertanto il client deve essere in grado di gestire correttamente la modifica. Il cloaking dell’origine blocca solo le richieste che vanno direttamente all’origine, ad esempio:

* Produzione

```php
mywebsite.com.c.abcdefghijkl.ent.magento.cloud
```

* Staging

```php
mcstaging2.mywebsite.com.c.abcdefghijkl.dev.ent.magento.cloud
```

* StagingX

```php
mcstagingX.mywebsite.com.c.abcdefghijkl.X.dev.ent.magento.cloud
```

In questo esempio, il client sarà comunque in grado di accedere all&#39;API se modifica l&#39;URL in ``mywebsite.com``:

```php
mywebsite.com/rest/default/V1/integration/admin/token?username=XXXX&password=XXXXX;
mywebsite.com/rest/default/V1/orders/
mywebsite.com/rest/default/V1/products/
mywebsite.com/rest/default/V1/inventory/source-items
```

## Questa modifica influirà sull&#39;implementazione e sui tempi di inattività?

No, questa modifica **NON** influisce sulla distribuzione e sui tempi di inattività.

## Se il progetto dispone di più ambienti di staging, il cloaking dell&#39;origine verrà applicato a tutti gli ambienti di staging?

Sì, se il progetto dispone di più ambienti di staging, la modifica verrà applicata a tutti gli ambienti di staging.
