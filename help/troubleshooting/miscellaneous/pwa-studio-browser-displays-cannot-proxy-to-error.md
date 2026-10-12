---
title: 'PWA Studio: nel browser viene visualizzato l’errore "Impossibile eseguire il proxy su"'
description: Questo argomento descrive una soluzione quando il browser Web visualizza un "*Impossibile eseguire il proxy a*" e la console visualizza un
exl-id: de689633-34b8-4a25-bbd0-a58742c4d03c
feature: Console
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: c4af0798-d497-5e6b-8380-19812c26d00a
    internal-label: Console
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%
---
# PWA Studio: nel browser viene visualizzato l’errore &quot;Impossibile eseguire il proxy su&quot;

In questo argomento viene illustrata una soluzione quando nel browser viene visualizzato un &quot;*Impossibile eseguire il proxy a*&quot; e nella console viene visualizzato un

```
ENOTFOUND
```

Errore durante l’utilizzo di Progressive Web App (PWA) Studio per Adobe Commerce.

## Prodotti e versioni interessati

* PWA Studio per Adobe Commerce

## Problema

<u>Passaggio da riprodurre</u>:

* Carica il tuo archivio Adobe Commerce in un browser.

<u>Risultato previsto</u>:

* L’archivio Adobe Commerce viene caricato normalmente nel browser.

<u>Risultato effettivo</u>:

* Nel browser viene visualizzato l&#39;errore &quot;*Impossibile eseguire il proxy a*&quot; e nella console viene visualizzato un errore simile al seguente:

```
    ENOTFOUND
```


## Causa

NodeJS non è in grado di risolvere il nome host dell’archivio Adobe Commerce.

## Soluzione

1. Assicurati che il tuo archivio Adobe Commerce venga caricato in più di un browser web.
1. Se si esegue un server DNS locale o una VPN, aggiungere una voce al file host (che si trova in `/etc/hosts`) e mappare manualmente questo dominio ([Istruzioni generiche sulla modifica del file host](https://linuxize.com/post/how-to-edit-your-hosts-file/)) in modo che NodeJS possa risolverlo.

## Lettura correlata

* [Documentazione di PWA Studio per Adobe Commerce](https://developer.adobe.com/commerce/pwa-studio/)
* [Strumenti e librerie](https://developer.adobe.com/commerce/pwa-studio/guides/project/tools-libraries/)
