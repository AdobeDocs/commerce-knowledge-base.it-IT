---
title: Sincronizza dati e file di produzione con staging o staging con l'integrazione
description: Questo articolo spiega come sincronizzare l’ambiente di produzione fino alla gestione temporanea su Adobe Commerce sull’infrastruttura cloud; questo non è possibile.
exl-id: e3d001d1-1b2a-41b5-9b4a-00e53dc9d001
feature: Integration, Build
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# Sincronizza dati e file di produzione con staging o staging con l&#39;integrazione

Questo articolo spiega come sincronizzare l’ambiente di produzione fino alla gestione temporanea su Adobe Commerce nell’infrastruttura cloud; ciò non è possibile tramite l’interfaccia utente o l’interfaccia della riga di comando cloud di Magento.

## Prodotti e versioni interessati

* Adobe Commerce sull’infrastruttura cloud 2.3.x, 2.4.x

## Per sincronizzare i dati da un ambiente all&#39;altro

Per sincronizzare i dati, è necessario scaricare manualmente il database dall&#39;ambiente di origine. Per trasferire i dati in un altro ambiente, devi quindi caricare il dump di origine nell’ambiente di destinazione e importarlo. Per ulteriori informazioni, consulta [Importare codice Adobe Commerce in un progetto Cloud > Importare database Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/staging-production) nella documentazione per gli sviluppatori.

Per l’architettura del piano Pro di Adobe Commerce su infrastruttura cloud, puoi anche eseguire la sincronizzazione da Staging e Produzione al ramo principale dell’integrazione. Questa sincronizzazione richiama e invia solo codice, non dati. Per sincronizzare i dati, devi scaricare i dati del database e inviarli al database di un altro ambiente.

>[!WARNING]
>
>La sincronizzazione del database non può essere eseguita nei cluster Pro Staging e Production.

## Per sincronizzare i file da un ambiente all&#39;altro

Per sincronizzare i file da un ambiente all&#39;altro, utilizzare il comando `rsync`. Per ulteriori informazioni, vedere [Distribuire il codice ed eseguire la migrazione di file e dati statici > Eseguire la migrazione di file utilizzando rsync](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/staging-production#migrate-files-using-rsync) nella documentazione per gli sviluppatori.

>[!NOTE]
>
>Se desideri sincronizzare il codice da Integration a Staging, devi farlo dal ramo Integration. Per i passaggi, consulta [Sincronizzazione dall&#39;ambiente padre](/docs/commerce-cloud-service/user-guide/project/console-branches.html#sync-an-environment) nella documentazione per gli sviluppatori.
