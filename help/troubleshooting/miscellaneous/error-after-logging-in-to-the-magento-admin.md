---
title: Errore dopo l’accesso all’amministrazione di Commerce
description: In questo articolo viene fornita una soluzione al problema per cui viene visualizzato un messaggio di errore in cui si informa che l'URL richiesto non è stato trovato nel server.
exl-id: f52b383b-87f2-4216-9bf4-e765db31ca6b
feature: Admin Workspace
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '144'
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

[Best practice per la modifica delle tabelle del database](https://experienceleague.adobe.com/it/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) nel playbook di implementazione di Commerce
