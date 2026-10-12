---
title: Nuovi ambienti messi in produzione quando vengono inviati da Git
description: Questo articolo fornisce una soluzione per il problema in cui i nuovi ambienti vengono inseriti nell’ambiente di produzione su Adobe Commerce sull’infrastruttura cloud quando vengono inviati dal sistema di controllo delle versioni Git.
exl-id: 279cd6d8-fd45-45ba-8456-8b397a01976f
feature: Cloud, Paas
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%
---
# Nuovi ambienti messi in produzione quando vengono inviati da Git

Questo articolo fornisce una soluzione per il problema in cui i nuovi ambienti vengono inseriti nell’ambiente di produzione su Adobe Commerce sull’infrastruttura cloud quando vengono inviati dal sistema di controllo delle versioni Git.

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud, [tutte le versioni supportate](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problema

<u>Prerequisiti</u>:

Disporre di un clone locale controllato da Git del progetto.

<u>Passaggi da riprodurre</u>:

È necessario creare un ramo di integrazione dal ramo di staging:

1. Passare al ramo di gestione temporanea eseguendo il comando seguente nella shell locale: `git checkout staging`
1. Creare un ramo di integrazione dal ramo di gestione temporanea eseguendo il comando seguente nella shell locale: `git checkout -b <branch>`
1. Eseguire il push del ramo all&#39;archivio remoto e impostare un ramo upstream eseguendo il comando seguente nella shell locale: `git push --set-upstream origin <branch>`

<u>Risultati previsti</u>:

Il nuovo ramo viene creato nel ramo di staging.

<u>Risultati effettivi</u>:

Il nuovo ramo è stato creato sotto il ramo di produzione.

## Causa

Questo non è un bug. Per impostare un ramo principale per un altro ramo, il commerciante deve utilizzare l’interfaccia della riga di comando cloud di Magento.

## Soluzione

Un ramo padre può essere impostato solo dopo che il commerciante ha inviato e attivato un ramo appena creato. Consulta [Adobe Commerce su infrastruttura cloud > Integrazione bitbucket](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/dev-tools/integrations/bitbucket#create-a-cloud-branch) nella documentazione per sviluppatori.

Per aggiornare un elemento padre per il ramo esistente sul server, utilizzare il comando `magento-cloud environment:info` nell&#39;interfaccia CLI di Magento-Cloud.

Esempio di utilizzo:

`magento-cloud environment:info parent Staging`

In questo modo il ramo padre verrà impostato su &quot;Staging&quot; per il ramo attualmente estratto.

## Lettura correlata

* [Adobe Commerce su infrastruttura cloud > CLI di magento-cloud](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli/cloud-cli-overview) nella documentazione per gli sviluppatori.
