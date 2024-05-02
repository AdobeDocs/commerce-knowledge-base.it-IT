---
title: Il nuovo dominio viene reindirizzato al dominio predefinito
description: Questo articolo corregge il problema relativo al reindirizzamento del nuovo dominio al dominio predefinito nell’ambiente esistente o in un ambiente diverso.
exl-id: 88e9eb3f-9b82-4ca3-aa80-e49f360b3eb9
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---

# Il nuovo dominio viene reindirizzato al dominio predefinito

Questo articolo corregge il problema relativo al reindirizzamento del nuovo dominio al dominio predefinito nell’ambiente esistente o in un ambiente diverso.

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud pro (tutte le versioni)

## Problema

Il nuovo dominio viene reindirizzato al dominio predefinito nell’ambiente corrente o al dominio predefinito di un altro ambiente.

## Causa

Ciò si verifica quando le variabili non vengono aggiornate dopo l’aggiunta di un nuovo dominio o il [!DNL Fastly] il servizio è stato configurato nell&#39;ambiente.

## Soluzione

1. Se il dominio viene reindirizzato nello stesso ambiente, assicurati di aver configurato [Variabili](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#modify-variables).
1. Se il dominio viene reindirizzato a un altro ambiente, verifica di aver configurato il [!DNL Fastly] eseguendo il comando seguente: `bin/magento fastly:conf:get -s`

>[!NOTE]
>
>È possibile trovare [!DNL Fastly] credenziali API effettuando l’accesso a ogni ambiente (Staging/Produzione) e controllando il `/mnt/shared/fastly_tokens.txt` file. Per ulteriori informazioni, consulta [configura [!DNL Fastly] servizi](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) nella Guida all’infrastruttura cloud di Commerce.

Se entrambe le configurazioni precedenti sono corrette, invia un ticket di supporto.

## Lettura correlata

* [Elenco di controllo per la configurazione di un nuovo dominio](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/checklist-for-setting-up-a-new-domain.html) nella nostra knowledge base di supporto.
