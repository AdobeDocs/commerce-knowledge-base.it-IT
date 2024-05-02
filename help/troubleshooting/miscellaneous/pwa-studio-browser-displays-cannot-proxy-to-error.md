---
title: '"PWA Studi: nel browser viene visualizzato l’errore "Impossibile eseguire il proxy su"'
description: Questo argomento descrive una soluzione quando il browser Web visualizza un "*Impossibile eseguire il proxy a*" e la console visualizza un
exl-id: de689633-34b8-4a25-bbd0-a58742c4d03c
feature: Console
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 0%

---

# PWA Studi: nel browser viene visualizzato l’errore &quot;Impossibile eseguire il proxy su&quot;

In questo argomento viene illustrata una soluzione quando nel browser viene visualizzato un &quot;*Impossibile eseguire il proxy a*&quot; e la console visualizza un

```
ENOTFOUND
```

Errore durante l’utilizzo di Progressive Web App (PWA) Studio per Adobe Commerce.

## Prodotti e versioni interessati

* PWA Studi per Adobe Commerce

## Problema

<u>Passaggio da riprodurre</u>:

* Carica il tuo archivio Adobe Commerce in un browser.

<u>Risultato previsto</u>:

* L’archivio Adobe Commerce viene caricato normalmente nel browser.

<u>Risultato effettivo</u>:

* Nel browser Web viene visualizzato il messaggio &quot;*Impossibile eseguire il proxy a*&quot;e la console visualizza un errore simile al seguente:

```
    ENOTFOUND
```


## Causa

NodeJS non è in grado di risolvere il nome host dell’archivio Adobe Commerce.

## Soluzione

1. Assicurati che il tuo archivio Adobe Commerce venga caricato in più di un browser web.
1. Se esegui un server DNS locale o una VPN, aggiungi una voce al file host (che si trova in `/etc/hosts`) e mappare manualmente questo dominio ([Istruzioni generiche sulla modifica di file host](https://linuxize.com/post/how-to-edit-your-hosts-file/)) in modo che NodeJS possa risolverlo.

## Lettura correlata

* [Documentazione di PWA Studi per Adobe Commerce](https://magento.github.io/pwa-studio/)
* [Strumenti e librerie](https://magento.github.io/pwa-studio/technologies/tools-libraries/)
