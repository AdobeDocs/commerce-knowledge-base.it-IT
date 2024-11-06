---
title: Campi bloccati (disattivati) nell’amministrazione di Commerce
description: Questo articolo fornisce una soluzione per i casi in cui non è possibile modificare i campi in Commerce Admin.
exl-id: 5fe0967a-4241-440b-bb0d-429fa5644bbc
feature: Admin Workspace
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# Campi bloccati (disattivati) nell’amministrazione di Commerce

Questo articolo fornisce una soluzione per i casi in cui non è possibile modificare i campi bloccati (disattivati) in Commerce Admin.

## Prodotti e versioni interessati

* Adobe Commerce on-premise 2.3.x, 2.4.x
* Adobe Commerce sull’infrastruttura cloud 2.3.x, 2.4.x

## Problema

Dopo aver salvato una modifica alla configurazione in `app/etc/env.php` o `app/etc/config.php`, non è possibile modificare l&#39;impostazione in Admin.

<u>Passaggi da riprodurre</u>:

Nota: questo è un esempio: il problema può interessare tutte le configurazioni salvate.

1. Il commerciante salva le credenziali dei metodi di consegna utilizzando il comando seguente nel terminale: `./vendor/bin/ece-tools config:dump`. Le credenziali verranno salvate nel file `app/etc/env.php`.
1. Il commerciante quindi tenta di modificare le credenziali in un secondo momento.

<u>Risultati previsti</u>:

Il commerciante può impostare i valori nelle impostazioni del campo Amministratore e salvarli.

<u>Risultati effettivi</u>:

I campi nell’Amministratore sono bloccati oppure è possibile modificare i valori, ma non vengono salvati nell’Amministratore.

## Causa

Quando la configurazione viene salvata in `env.php` o `config.php`, non sarà possibile modificare l&#39;impostazione in Admin. Per consentire la modifica dell&#39;impostazione, è necessario rimuovere la configurazione da `env.php` o `config.php`.

## Soluzione

Verificare che la configurazione non sia stata salvata in `app/etc/env.php` o `app/etc/config.php`. Se è stato salvato, effettuare le seguenti operazioni:

* `config.php` - Rimuovere l&#39;impostazione e quindi ridistribuire.
* `env.php` - Modificare l&#39;impostazione direttamente sul server e rimuoverla, quindi eseguire `bin/magento app:config:import`.

## Lettura correlata

* [Esporta la configurazione](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configuration-management/export-configuration) nella documentazione per gli sviluppatori.
* [Imposta i valori di configurazione](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configuration-management/set-configuration-values) nella documentazione per gli sviluppatori.
* [Adobe Commerce sull&#39;infrastruttura cloud: riduci i tempi di inattività dell&#39;implementazione con Configuration Management](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) nella knowledge base per il supporto.
