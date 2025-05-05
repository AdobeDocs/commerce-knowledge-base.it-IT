---
title: Errore di memoria insufficiente durante l'installazione o l'aggiornamento
description: In questo articolo vengono illustrate le soluzioni per l'errore di memoria insufficiente durante l'installazione o l'aggiornamento dei prodotti Adobe Commerce on-premise e Magento Open Source on-premise.
exl-id: c0ed8228-9357-4a3b-a102-1119386ea52a
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Errore di memoria insufficiente durante l&#39;installazione o l&#39;aggiornamento

In questo articolo vengono illustrate le soluzioni per l&#39;errore di memoria insufficiente durante l&#39;installazione o l&#39;aggiornamento dei prodotti Adobe Commerce on-premise e Magento Open Source on-premise.

## Prodotti e versioni interessati

* Adobe Commerce on-premise 2.3.x
* Magento Open Source locale 2.3.x

## Problema

Quando si installa o si aggiorna un&#39;applicazione Adobe Commerce o di Magento Open Source o componenti quali estensioni, temi o pacchetti di lingue mediante l&#39;Installazione guidata Web, viene visualizzato un errore simile al seguente:

```bash
Could not complete update {"components":[
{"name":"magento/module-bundle-sample-data","version":"100.1.0"}
]} successfully: proc_open(): fork failed - Cannot allocate memory
```

L’errore

```bash
proc_open(): fork failed - Cannot allocate memory
```

può essere visualizzato anche sulla riga di comando.

## Soluzione {#solution}

È consigliabile [allocare 2 GB di memoria a PHP](https://experienceleague.adobe.com/it/docs/commerce-operations/installation-guide/prerequisites/php-settings) nella documentazione per gli sviluppatori per verificare che l&#39;installazione o l&#39;aggiornamento abbiano esito positivo.

Se lo hai già fatto, crea un file di scambio sul computer. Un computer Linux utilizza *spazio di swap* se necessita di più risorse di memoria e la RAM è piena. Lo spazio di swap viene utilizzato per le pagine inattive in memoria.

Di seguito sono riportati solo i suggerimenti; potrebbero essere disponibili altre opzioni. Prima di continuare, consultare un amministratore di rete o un&#39;altra risorsa. È necessario eseguire i comandi per creare un file di scambio come utente con privilegi `root`.

### Scambia file su Ubuntu {#swap-file-on-ubuntu}

Utilizza il comando `fallocate` come descritto in questi riferimenti:

* [Come aggiungere lo scambio su Ubuntu 14.04 (Digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-ubuntu-14-04)
* [Come aggiungere spazio di scambio su Ubuntu 16.04 (Digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-16-04)
* [Domande frequenti su Swap (help.ubuntu.com)](https://help.ubuntu.com/community/SwapFaq)

### Scambia file su CentOS {#swap-file-on-centos}

Utilizza il comando `mkswap` come descritto in questi riferimenti:

* [Come aggiungere lo scambio su CentOS 6 (Digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-centos-6)
* [Come aggiungere lo scambio su CentOS 7 (Digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-centos-7)
* [Scambia spazio (portale clienti RedHat)](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Storage_Administration_Guide/ch-swapspace.html)
