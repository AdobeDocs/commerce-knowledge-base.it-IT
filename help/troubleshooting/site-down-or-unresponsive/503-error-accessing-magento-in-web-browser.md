---
title: Errore 503 durante l’accesso ad Adobe Commerce nel browser web
description: Questo articolo fornisce una possibile soluzione al problema relativo all’errore 503 che si verifica quando si tenta di accedere alla vetrina e/o all’amministratore di Adobe Commerce.
exl-id: 4232aa21-40c2-41b0-9fb0-fc8cd4db8e39
feature: Storefront
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---

# Errore 503 durante l’accesso ad Adobe Commerce nel browser web

Questo articolo fornisce una possibile soluzione al problema relativo all’errore 503 che si verifica quando si tenta di accedere alla vetrina e/o all’amministratore di Adobe Commerce.

## Prodotti e versioni interessati

Adobe Commerce 2.3.x

## Problema {#symptoms}

<u>Passaggi da riprodurre</u>

(Prerequisiti: verificare che l&#39;archivio non sia in [modalità di manutenzione](https://experienceleague.adobe.com/it/docs/commerce-operations/configuration-guide/cli/set-mode#config-mode-show)).

Passa all’amministratore di Commerce o alla vetrina in un browser web.

<u>Risultato previsto</u>

La pagina viene caricata.

<u>Risultato effettivo</u>

Viene visualizzato l&#39;errore HTTP 503 (Servizio non disponibile). Apache `error.log` include il seguente messaggio:

*Comando &#39;Order&#39; non valido, probabilmente scritto in modo errato o definito da un modulo non incluso nella configurazione del server.*

## Causa {#details}

Il modulo di compatibilità Apache 2.4 `mod_access_compat` è disabilitato. Di conseguenza, le riscritture dell&#39;URL di Adobe Commerce non funzionano correttamente.

## Soluzione {#suggested-solution}

Abilitare il modulo Apache `mod_access_compat` e riavviare Apache eseguendo il comando seguente come utente con privilegi di radice:

```bash
a2enmod access_compat
service <name> restart
```

Su CentOS,

```bash
<name>
```

è

```bash
httpd
```

. Su Ubuntu,

```bash
<name>
```

è

```bash
apache2
```

.

## Lettura correlata {#additional-resources}

* [Documentazione di Apache su mod\_access\_compat](https://httpd.apache.org/docs/current/mod/mod_access_compat.html)
* [Documentazione di Apache su mod\_authz\_host](https://httpd.apache.org/docs/current/mod/mod_authz_host.html)
* [Ordine, Consenti, Nega dalla Guida definitiva di Apache](https://docstore.mik.ua/orelly/linux/apache/ch05_06.htm)
* [askubuntu.com](https://askubuntu.com/questions/335228/changes-in-apache-config-between-12-04-2-and-12-04-3-lts)
