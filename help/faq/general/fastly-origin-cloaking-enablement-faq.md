---
title: "[!DNL Fastly] domande frequenti sull’abilitazione del cloaking dell’origine"
description: Queste domande frequenti trattano domande comuni su [!DNL Fastly] abilitazione del cloaking dell’origine in Adobe Commerce (completamente implementata dal 2021).
exl-id: d608abe7-7d64-44ce-bea1-34b201c29113
source-git-commit: 1021a1ab81481f92e850bd49330f1742fe9a21f2
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# [!DNL Fastly] domande frequenti sull’abilitazione del cloaking dell’origine

Queste domande frequenti trattano domande comuni su [!DNL Fastly] abilitazione del cloaking dell’origine in Adobe Commerce (completamente implementata dal 2021).

## Cos’è [!DNL Fastly] occultamento origine?

Il cloaking dell’origine è una funzione di sicurezza che consente ad Adobe Commerce sull’infrastruttura cloud di bloccare qualsiasi [!DNL non-Fastly] traffico (per prevenire gli attacchi DDoS, vai all’infrastruttura cloud (origine).

## Quali sono i vantaggi del cloaking dell’origine?

Il cloaking dell&#39;origine è progettato per evitare che il traffico bypassi il [!DNL Fastly Web Application Firewall] (WAF) e la sua instradamento attraverso il flusso di **[!DNL Fastly]** > **Load Balancer** > **Istanze**. Con questa implementazione, tutto il traffico sarà di sicuro percorribile attraverso [!DNL Fastly] WAF e WAF interno integrati nel load balancer.

## Perché si sta verificando l’abilitazione del cloaking dell’origine?

Questa funzione è stata originariamente creata per avvantaggiare Adobe Commerce sull’infrastruttura cloud.

## Devo richiedere l’abilitazione del cloaking dell’origine per il mio progetto?

No. Questa funzione avrebbe dovuto essere già implementata in tutti i progetti cloud e, per impostazione predefinita, per tutti i progetti il cui provisioning è stato eseguito dal 2021, questa funzione sarebbe stata abilitata.

## Il cloaking dell&#39;origine cambia l&#39;indirizzo IP in uscita?

No, non è così.

## Il cloaking dell’origine influisce sull’API REST?

[!DNL Fastly] non memorizza in cache le chiamate API, pertanto il client deve accettare la modifica. Il cloaking dell’origine blocca solo le richieste che vanno direttamente all’origine, ad esempio:

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

In questo esempio, il client sarà ancora in grado di accedere all’API se modifica l’URL in ``mywebsite.com``:

```php
mywebsite.com/rest/default/V1/integration/admin/token?username=XXXX&password=XXXXX;
mywebsite.com/rest/default/V1/orders/
mywebsite.com/rest/default/V1/products/
mywebsite.com/rest/default/V1/inventory/source-items
```

## Questa modifica influirà sull&#39;implementazione e sui tempi di inattività?

No, questa modifica **NOT** influire sull’implementazione e sui tempi di inattività.

## Se il progetto dispone di più ambienti di staging, il cloaking dell&#39;origine verrà applicato a tutti gli ambienti di staging?

Sì, se il progetto dispone di più ambienti di staging, la modifica verrà applicata a tutti gli ambienti di staging.
