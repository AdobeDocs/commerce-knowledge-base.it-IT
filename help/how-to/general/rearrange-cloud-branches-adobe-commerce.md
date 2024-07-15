---
title: Riorganizzare i rami cloud in Adobe Commerce
description: Questo articolo descrive i passaggi da seguire per riorganizzare i rami cloud su Adobe Commerce, se non sono organizzati secondo la gerarchia corretta. Se i rami non sono organizzati nella gerarchia corretta, non sarà possibile eseguire l'unione nel ramo padre corretto, ma passerà al ramo padre esistente.
exl-id: 4fc0de96-da66-4634-a38a-6a1536855f8f
feature: Cloud
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Riorganizzare i rami cloud in Adobe Commerce

Questo articolo descrive i passaggi da seguire per riorganizzare i rami cloud su Adobe Commerce, se non sono organizzati secondo la gerarchia corretta. Se i rami non sono organizzati nella gerarchia corretta, non sarà possibile eseguire l&#39;unione nel ramo padre corretto, ma passerà al ramo padre esistente.

## Prodotti e versioni interessati:

* Adobe Commerce su infrastruttura cloud, 2.3.0-2.3.7-p2, 2.4.0-2.4.3-p1

## Organizzazione di filiali cloud

L’organizzazione gerarchica corretta per i rami è:

* [!DNL Master [main] > Production > Staging > Integration]
* [!DNL Master [main] > Production > Staging > Integration2]

## Soluzione per l’organizzazione errata dei rami cloud

Per riorganizzare i rami cloud:

1. Devi avere la mansione [[!DNL Super User]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html).
1. Installare il cloud magento [!DNL CLI] (se non lo si è fatto).
1. Esegui il seguente comando per i rami da spostare:
   `magento-cloud environment:info -e <branch to move> parent <target parent>`

Nota: è possibile specificare il ramo padre quando si crea un nuovo ramo. Per i passaggi, consulta [Guida introduttiva alla creazione di rami](https://devdocs.magento.com/cloud/env/environments-start.html#getstarted) nella documentazione per gli sviluppatori.

È possibile creare un nuovo ramo dell&#39;ambiente utilizzando il comando dell&#39;ambiente magento-cloud `branch <environment-name> <parent-environment-ID>`.

La creazione e l’attivazione di un nuovo ramo dell’ambiente potrebbe richiedere un po’ di tempo.

## Lettura correlata

[Gestisci i rami con  [!DNL CLI]](https://devdocs.magento.com/cloud/env/environments-start.html) nella documentazione per gli sviluppatori.
