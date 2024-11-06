---
title: Nuovi ambienti messi in produzione quando vengono inviati da Git
description: Questo articolo fornisce una soluzione per il problema in cui i nuovi ambienti vengono inseriti nell’ambiente di produzione su Adobe Commerce sull’infrastruttura cloud quando vengono inviati dal sistema di controllo delle versioni Git.
exl-id: 279cd6d8-fd45-45ba-8456-8b397a01976f
feature: Cloud, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '296'
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

Un ramo padre può essere impostato solo dopo che il commerciante ha inviato e attivato un ramo appena creato. Consulta [Adobe Commerce su infrastruttura cloud > Integrazione bitbucket](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/integrations/bitbucket#create-a-cloud-branch) nella documentazione per sviluppatori.

Per aggiornare un elemento padre per il ramo esistente sul server, utilizzare il comando `magento-cloud environment:info` nell&#39;interfaccia CLI di Magento-Cloud.

Esempio di utilizzo:

`magento-cloud environment:info parent Staging`

In questo modo il ramo padre verrà impostato su &quot;Staging&quot; per il ramo attualmente estratto.

## Lettura correlata

* [Adobe Commerce su infrastruttura cloud > CLI di magento-cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli/cloud-cli-overview) nella documentazione per gli sviluppatori.
