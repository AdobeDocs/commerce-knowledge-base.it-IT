---
title: 'PWA Studio: Webpack si blocca prima di iniziare la compilazione'
description: In questo articolo viene illustrata una soluzione consigliata per l'interruzione prolungata di un codice JavaScript [Webpack](https://developer.adobe.com/commerce/pwa-studio/guides/project/tools-libraries/#webpack) prima di iniziare la compilazione in Progressive Web App Studio (PWA Studio).
exl-id: 692eeafa-9289-4d66-9f2f-1e0fe36e681d
feature: Configuration
role: Developer
source-git-commit: 40766238a7ea748bff86decf75cddec28fe63bb9
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# PWA Studio: Webpack si blocca prima di iniziare la compilazione

In questo articolo viene illustrata la soluzione suggerita per l&#39;interruzione prolungata di un javascript [Webpack](https://developer.adobe.com/commerce/pwa-studio/guides/project/tools-libraries/#webpack) prima di iniziare la compilazione in Progressive Web App Studio (PWA Studio).

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

<u>Prerequisiti</u>: configura una vetrina PWA Studio, ad esempio Venia, con un&#39;istanza Adobe Commerce locale ed esegui una

```yaml
build
```

o

```yaml
watch
```

comando.

<u>Risultato previsto</u>:

* Se si utilizza il comando `build`, vengono generati normalmente gli artefatti di build per Venia.
* Se si utilizza il comando `watch`, la vetrina di Venia viene avviata normalmente.

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

* [Webpack Javascript: Concetti](https://webpack.js.org/concepts/)
* [Configurazione vetrina Venia](https://developer.adobe.com/commerce/pwa-studio/guides/packages/venia/)
* [PWA Buildpack](https://developer.adobe.com/commerce/pwa-studio/guides/packages/buildpack/)
* [Interfaccia riga di comando buildpack](https://developer.adobe.com/commerce/pwa-studio/api/buildpack/cli/)
* [Strumenti e librerie: buildpack](https://developer.adobe.com/commerce/pwa-studio/guides/project/tools-libraries/#webpack)
