---
title: 'API web: impossibile elaborare le richieste con più di 20 elementi nell’array'
description: Questo articolo fornisce una soluzione al problema che impedisce all’API web di elaborare un messaggio contenente più di 20 elementi nell’array per Adobe Commerce 2.4.3.
exl-id: 7e6b3fe8-3133-4773-afa7-fbfdd98ecde9
feature: REST
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# API web: impossibile elaborare le richieste con più di 20 elementi nell’array

Questo articolo fornisce una soluzione al problema che impedisce all’API web di elaborare un messaggio contenente più di 20 elementi nell’array per Adobe Commerce 2.4.3.

## Prodotti e versioni interessati:

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 e 2.3.7-p1
* Magento Open Source 2.4.3 e 2.3.7-p1

## Problema

API Web: impossibile elaborare il messaggio (ad esempio, Stock Update) che contiene più di 20 elementi nell’array.

## Causa

In Adobe Commerce 2.4.3, la limitazione della frequenza incorporata è stata aggiunta alle API di Magento per prevenire gli attacchi Denial of Service (DoS).

Per impostazione predefinita, è disponibile la seguente limitazione di frequenza API integrata:

* Le richieste REST contenenti input che rappresentano un elenco di entità sono limitate a un massimo predefinito di 20 entità
* Le query REST e GraphQL che consentono risultati impaginati sono limitate a un massimo predefinito di 300 elementi per pagina

## Soluzione

Per disabilitare i limiti di input nella richiesta API REST, applica una delle seguenti patch (a seconda della versione):

* [MC-43048__set_rate_limits__2.3.7-p1.patch.zip](assets/MC-43048__set_rate_limits__2.3.7-p1.patch.zip)
* [MC-43048__set_rate_limits__2.4.3.patch.zip](assets/MC-43048__set_rate_limits__2.4.3.patch.zip)

### Versioni compatibili di Adobe Commerce

Le patch sono state create per:

* Adobe Commerce sull’infrastruttura cloud 2.4.3 e 2.3.7-p1
* Adobe Commerce on-premise 2.4.3 e 2.3.7-p1

Le patch non sono compatibili con altre versioni di Adobe Commerce.

### Come applicare il cerotto

Decomprimi il download `.zip` e applicare la patch come descritto in [Come applicare una patch del compositore fornita dall&#39;Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).

>[!WARNING]
>
>Se sospetti che il tuo archivio stia avendo un attacco DoS, Adobe consiglia di abbassare i limiti di input predefiniti a un valore inferiore per imporre restrizioni sul numero di risorse che possono essere richieste.  È possibile personalizzare i limiti predefiniti a livello di programmazione utilizzando [argomenti del costruttore di classe](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/di-xml-file.html)
>come descritto nella documentazione per gli sviluppatori: [Sicurezza API > Limitazione velocità > Numero massimo di input del parametro](https://devdocs.magento.com/guides/v2.4/get-started/api-security.html#rate-limiting).

## Lettura correlata

[Sicurezza API > Limitazione di frequenza](https://devdocs.magento.com/guides/v2.4/get-started/api-security.html#rate-limiting) nella documentazione per gli sviluppatori.
