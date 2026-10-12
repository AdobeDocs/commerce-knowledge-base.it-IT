---
title: Il nuovo dominio viene reindirizzato al dominio predefinito
description: Questo articolo corregge il problema relativo al reindirizzamento del nuovo dominio al dominio predefinito nell’ambiente esistente o in un ambiente diverso.
exl-id: 88e9eb3f-9b82-4ca3-aa80-e49f360b3eb9
feature: Configuration
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%
---
# Il nuovo dominio viene reindirizzato al dominio predefinito

Questo articolo corregge il problema relativo al reindirizzamento del nuovo dominio al dominio predefinito nell’ambiente esistente o in un ambiente diverso.

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud pro (tutte le versioni)

## Problema

Il nuovo dominio viene reindirizzato al dominio predefinito nell’ambiente corrente o al dominio predefinito di un altro ambiente.

## Causa

Ciò si verifica quando le variabili non vengono aggiornate dopo l&#39;aggiunta di un nuovo dominio o quando nell&#39;ambiente è stato configurato il servizio [!DNL Fastly] errato.

## Soluzione

1. Se il dominio viene reindirizzato nello stesso ambiente, verificare di aver configurato le [variabili](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#modify-variables).
1. Se il dominio sta reindirizzando a un altro ambiente, verificare di aver configurato il servizio [!DNL Fastly] corretto eseguendo il comando seguente: `bin/magento fastly:conf:get -s`

>[!NOTE]
>
>È possibile trovare le credenziali API [!DNL Fastly] accedendo a ogni ambiente (Gestione temporanea/Produzione) e controllando il file `/mnt/shared/fastly_tokens.txt`. Per ulteriori informazioni, vedere [configure [!DNL Fastly] services](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) nella Guida all&#39;infrastruttura cloud di Commerce.

Se entrambe le configurazioni precedenti sono corrette, invia un ticket di supporto.

## Lettura correlata

* [Elenco di controllo per la configurazione di un nuovo dominio](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/checklist-for-setting-up-a-new-domain.html) nella Knowledge Base di supporto.
