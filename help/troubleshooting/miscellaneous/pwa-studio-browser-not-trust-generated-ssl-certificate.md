---
title: 'PWA Studio: il browser non considera attendibile il certificato SSL generato'
description: Questo articolo fornisce una soluzione a un avviso di certificato SSL generato e non attendibile nel browser quando si passa a un’istanza locale della vetrina PWA Studio durante lo sviluppo.
exl-id: b7bfe1e6-5832-4472-9e51-f04b8583428a
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
source-wordcount: '303'
ht-degree: 0%
---
# PWA Studio: il browser non considera attendibile il certificato SSL generato

Questo articolo fornisce una soluzione a un avviso di certificato SSL generato e non attendibile nel browser quando si passa a un’istanza locale della vetrina PWA Studio durante lo sviluppo.

## Prodotti e versioni interessati

PWA Studio per Adobe Commerce

## Problema

Il browser non considera attendibile il certificato SSL generato della vetrina PWA Studio locale.

## Causa

Navigazione al sito di sviluppo/staging.

## Soluzione

Nel progetto storefront, esegui il comando per aggiungere un nome host personalizzato e un certificato SSL all’istanza di sviluppo locale:

```sh
yarn buildpack create-custom-origin ./
```

La generazione dei certificati è gestita da [devcert](https://github.com/davewasmer/devcert). Dipende da OpenSSL, quindi assicurati di avere una versione corrente di openssl sul tuo sistema utilizzando il seguente comando:

`openssl version`

La versione deve essere 1.0 o successiva (o LibreSSL 2, nel caso di OSX High Sierra).

Puoi installare versioni successive di OpenSSL con [Homebrew](https://brew.sh/) su OSX, [Chocolatey](https://chocolatey.org/) su Windows o il gestore di pacchetti della distribuzione Linux.

Se esegui Linux, assicurati che `libnss3-tools` (o l&#39;equivalente) sia installato nel tuo sistema. Ulteriori informazioni fornite in questa sezione del file readme [devcert](https://github.com/davewasmer/devcert#skipcertutil).

Alcuni utenti hanno suggerito di eliminare la cartella devcert per attivare la rigenerazione dei certificati.

* Per gli utenti di MacOS, questa cartella si trova in genere in: `{{~/Library/Application Support/devcert }}`
* Per gli utenti di Windows, questa cartella si trova in genere all&#39;indirizzo: `${User}\AppData\Local\devcert`

## Lettura correlata nella knowledge base del supporto

* [PWA Studio: errore di attendibilità del certificato autofirmato](https://support.magento.com/hc/en-us/articles/360038973172)
* [PWA Studio: Webpack si blocca prima di iniziare la compilazione](/help/troubleshooting/miscellaneous/pwa-studio-webpack-hangs-before-beginning-compilation.md)
* [PWA Studio: nel browser viene visualizzato l’errore &quot;Impossibile eseguire il proxy su&quot;](/help/troubleshooting/miscellaneous/pwa-studio-browser-displays-cannot-proxy-to-error.md)
* [PWA Studio: errori di convalida durante l’esecuzione della modalità sviluppatore](/help/troubleshooting/miscellaneous/pwa-studio-validation-errors-when-running-developer-mode.md)
