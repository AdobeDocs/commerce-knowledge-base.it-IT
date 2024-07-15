---
title: "PWA Studio: Webpack si blocca prima di iniziare la compilazione"
description: In questo articolo viene illustrata una soluzione consigliata per l'interruzione prolungata di un codice JavaScript [Webpack](https://magento.github.io/pwa-studio/technologies/tools-libraries/#webpack) prima di iniziare la compilazione in Progressive Web App Studio (PWA Studio).
exl-id: 692eeafa-9289-4d66-9f2f-1e0fe36e681d
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# PWA Studio: Webpack si blocca prima di iniziare la compilazione

In questo articolo viene illustrata una soluzione suggerita per la sospensione prolungata di un codice JavaScript [Webpack](https://magento.github.io/pwa-studio/technologies/tools-libraries/#webpack) prima di iniziare la compilazione in Progressive Web App Studio (PWA Studio).

## Prodotti e versioni interessati

* PWA Studio

## Problema

[Verificare la versione più recente di pwa-buildpack](https://github.com/magento/pwa-studio/tree/master/packages/pwa-buildpack) e

```yaml
pwa-buildpack
```

il numero di versione sarà accanto all&#39;elenco dei nomi file `package.json`. Se si dispone di una versione precedente di

```yaml
pwa-buildpack
```

progetto, il webpack potrebbe bloccarsi per molto tempo prima di iniziare la compilazione.

<u>Passaggi da riprodurre</u>:

<u>Prerequisiti</u>: configura una vetrina PWA Studi, ad esempio Venia, con un&#39;istanza Adobe Commerce locale ed esegui una

```yaml
build
```

o

```yaml
watch
```

comando.

<u>Risultato previsto</u>:

* Se utilizzi il    ```yaml    build    ```    genera gli artefatti di build per Venia normalmente.
* Se utilizzi il    ```yaml    watch    ```    comando, avvia la vetrina Venia normalmente.

<u>Risultato effettivo</u>:

Il tuo

```yaml
build
```

o

```yaml
watch
```

Il comando apparirà in stallo e non verrà completato, né verranno visualizzati errori.

## Soluzioni

Aggiorna il progetto con il seguente comando:

```yaml
yarn upgrade
```

Verificare di disporre di una versione corrente di openssl nel sistema utilizzando il comando seguente:

```yaml
openssl version
```

La versione deve essere 1.0 o successiva (o LibreSSL 2, nel caso di OSX High Sierra.).

Puoi installare versioni successive di OpenSSL con [Homebrew](https://brew.sh/) su OSX, [Chocolatey](https://chocolatey.org/) su Windows o il gestore di pacchetti della distribuzione Linux.

## Lettura correlata

* [Webpack JavaScript: Concetti](https://webpack.js.org/concepts/)
* [Configurazione vetrina Venia](https://magento.github.io/pwa-studio/venia-pwa-concept/setup/)
* [PWA Buildpack](https://magento.github.io/pwa-studio/pwa-buildpack/)
* [interfaccia della riga di comando buildpack](https://magento.github.io/pwa-studio/pwa-buildpack/reference/buildpack-cli/)
* [Strumenti e librerie: buildpack](https://magento.github.io/pwa-studio/technologies/tools-libraries/#webpack)
