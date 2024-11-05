---
title: Errore di pagina vuota o ciclo di reindirizzamento durante l’accesso a storefront o Commerce Admin
description: Questo articolo fornisce una soluzione al problema che si verifica quando si accede alla vetrina o al backend di Adobe Commerce e si ottiene una pagina vuota o un ciclo di reindirizzamento.
exl-id: 65869de2-1939-481b-844b-69122345b407
feature: Admin Workspace, Cache, Storefront
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# Errore di pagina vuota o ciclo di reindirizzamento durante l’accesso a storefront o Commerce Admin

Questo articolo fornisce una soluzione al problema che si verifica quando si accede alla vetrina o al backend di Adobe Commerce e si ottiene una pagina vuota o un ciclo di reindirizzamento.

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud, tutte le versioni
* Adobe Commerce on-premise, tutte le versioni
* Magento Open Source, tutte le versioni

## Problema

<u>Passaggi da riprodurre</u>

Apri una pagina vetrina o amministrazione.

<u>Risultato previsto</u>

Viene visualizzata la pagina.

<u>Risultato effettivo</u>

La pagina è vuota o visualizza il messaggio di errore *&quot;Questa pagina Web ha un ciclo di reindirizzamento&quot;*.

## Causa

Uno dei motivi più probabili del problema è che Adobe Commerce è impostato per il reindirizzamento da un URL non sicuro a un URL protetto, ma come valore per l’impostazione dell’URL protetto viene fornito un URL non protetto.

Per risolvere il problema, è necessario correggere il valore del collegamento protetto.

## Soluzione

Per assicurarsi che questa sia la causa del problema, procedere come segue:

1. Controllare il valore `web/secure/enable_upgrade_insecure` , `web/secure/use_in_adminhtml` (se si è verificato il problema di reindirizzamento vuoto/loop in Admin) o `web/secure/use_in_frontend` (se si è verificato il problema di reindirizzamento vuoto/loop nella vetrina) nella tabella del database `'core_config_data'`.
   * Se `web/secure/enable_upgrade_insecure` è impostato su &quot;1&quot;, Adobe Commerce è configurato per aggiungere l&#39;intestazione di risposta `Content-Security-Policy: upgrade-insecure-requests`, indicando così ai browser di utilizzare HTTPS, reindirizzando tutte le query provenienti da HTTP
a HTTPS, sia per Admin che per storefront.
   * Se `web/secure/use_in_adminhtml` è impostato su &quot;1&quot;, Adobe Commerce restituisce i reindirizzamenti HTTPS per tutte le richieste HTTP per le pagine di amministrazione.
   * Se `web/secure/use_in_frontend` è impostato su &quot;1&quot;, Adobe Commerce restituisce i reindirizzamenti HTTPS per tutte le richieste HTTP per le pagine iniziali dell&#39;archivio.
1. Controllare i valori `web/secure/base_url` e `web/unsecure/base_url` nella tabella `'core_config_data'`. Se iniziano entrambi con    `http`, è necessario correggere il valore &quot;secure&quot;.

Risoluzione del problema:

1. Imposta il valore che inizia con `https` per `web/secure/base_url.`
1. Per applicare le modifiche, pulire la cache di configurazione eseguendo il comando seguente:

   ```bash
   php <your_magento_install_dir>/bin/magento cache:clean config
   ```

## Lettura correlata

[Best practice per la modifica delle tabelle del database](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) nel playbook di implementazione di Commerce
