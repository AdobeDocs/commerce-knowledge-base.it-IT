---
title: Errore dopo l’accesso all’amministrazione di Commerce
description: In questo articolo viene fornita una soluzione al problema per cui viene visualizzato un messaggio di errore in cui si informa che l'URL richiesto non è stato trovato nel server.
exl-id: f52b383b-87f2-4216-9bf4-e765db31ca6b
feature: Admin Workspace
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%
---
# Errore dopo l’accesso all’amministrazione di Commerce

In questo articolo viene fornita una soluzione al problema per cui viene visualizzato un messaggio di errore in cui si informa che l&#39;URL richiesto non è stato trovato nel server.

## Dettagli

L&#39;URL richiesto /magento2index.php/admin/admin/dashboard/index/key/0c81957145a968b697c32a846598dc2e/ non è stato trovato in questo server.

Si noti l&#39;assenza di una barra tra `magento2` e `index.php` nell&#39;URL.

## Soluzione

L&#39;URL di base non è corretto. L’URL di base deve:

* Inizia con `http://` o `https://`
* Termina con una barra ( `/` )
* Usa le stesse maiuscole e minuscole del record `web/unsecure/base_url` nella tabella del database `core_config_data`

Rieseguire l&#39;installazione utilizzando un valore valido.

## Lettura correlata

[Best practice per la modifica delle tabelle del database](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) nel playbook di implementazione di Commerce
