---
title: Errore dopo l’accesso all’amministrazione di Commerce
description: In questo articolo viene fornita una soluzione al problema per cui viene visualizzato un messaggio di errore in cui si informa che l'URL richiesto non è stato trovato nel server.
exl-id: f52b383b-87f2-4216-9bf4-e765db31ca6b
feature: Admin Workspace
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# Errore dopo l’accesso all’amministrazione di Commerce

In questo articolo viene fornita una soluzione al problema per cui viene visualizzato un messaggio di errore in cui si informa che l&#39;URL richiesto non è stato trovato nel server.

## Dettagli

L&#39;URL richiesto /magento2index.php/admin/admin/dashboard/index/key/0c81957145a968b697c32a846598dc2e/ non è stato trovato in questo server.

Si noti l&#39;assenza di una barra tra `magento2` e `index.php` nell’URL.

## Soluzione

L&#39;URL di base non è corretto. L’URL di base deve:

* Inizia con `http://` o `https://`
* Termina con una barra ( `/` )
* Usa le stesse maiuscole e minuscole di `web/unsecure/base_url` registrare in `core_config_data` tabella di database

Rieseguire l&#39;installazione utilizzando un valore valido.
