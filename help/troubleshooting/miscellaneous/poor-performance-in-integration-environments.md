---
title: Prestazioni insoddisfacenti negli ambienti di integrazione
description: Questo articolo fornisce una soluzione per il problema in cui gli ambienti di integrazione Pro e gli ambienti di staging Starter hanno prestazioni insoddisfacenti.
feature: Integration, Staging
role: Developer
exl-id: 46110dbc-2f54-4654-95e2-39e8ae1e6979
source-git-commit: 139c2836ba36686357c7a5458a36550c7b1273c1
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Prestazioni insoddisfacenti negli ambienti di integrazione

Questo articolo fornisce una soluzione per il problema in cui gli ambienti di integrazione Pro e gli ambienti di staging Starter hanno prestazioni insoddisfacenti.

## Prodotti e versioni interessati:

* Adobe Commerce su infrastruttura cloud (tutte le versioni)

## Problema

Le prestazioni dell&#39;ambiente di integrazione Pro o dell&#39;ambiente di staging Starter sono insoddisfacenti.

## Causa

A seconda delle dimensioni del catalogo o dei dati o dei requisiti delle integrazioni o personalizzazioni di terze parti, le risorse disponibili negli ambienti di integrazione potrebbero aver superato il limite consentito.

## Soluzione

Per risolvere i problemi relativi alle prestazioni, assicurati di seguire le best practice per prestazioni ottimali nell’ambiente di integrazione. Per migliorare l’integrazione, potrebbe essere inoltre necessario richiedere un aggiornamento degli ambienti.

Determinare innanzitutto se l&#39;ambiente si trova nella [configurazione di integrazione avanzata](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27242).

* [Architettura Pro](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment)
* [Architettura Starter](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#staging-environment)

Controllare il registro di distribuzione utilizzando uno di questi metodi.

### Metodo 1:

Esegui il comando seguente utilizzando Cloud CLI:

`magento-cloud activity:log -e <branch name>`

### Metodo 2:

Controllare il registro di distribuzione più recente per tale ambiente nella [Console cloud](https://console.adobecommerce.com).

Alla fine del registro di distribuzione, se noti qualcosa di simile (la prima riga mostra size=XL e le righe rimanenti mostrano size=L), significa che sei nella configurazione dell’integrazione avanzata.

```
Environment configuration
mymagento (type: php:8.2, size: XL, disk: 5120)
mysql (type: mysql:10.6, size: L, disk: 5120)
redis (type: redis:7.2, size: L)
opensearch (type: opensearch:2, size: L, disk: 1024)
rabbitmq (type: rabbitmq:3.12, size: L, disk: 1024)
```

Se non sei nella configurazione dell&#39;integrazione avanzata, puoi [richiedere il miglioramento/aggiornamento](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27242).
Se ti trovi già nella configurazione di Integrazione avanzata o riscontri ancora problemi di prestazioni dopo l’aggiornamento, assicurati di seguire le best practice per prestazioni ottimali nell’ambiente di integrazione:

* [Architettura Pro](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment)
* [Architettura Starter](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#staging-environment)

Se hai soddisfatto le raccomandazioni precedenti, [invia una richiesta di supporto](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket) per ulteriore assistenza.
