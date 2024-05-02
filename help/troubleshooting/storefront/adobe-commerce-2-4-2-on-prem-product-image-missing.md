---
title: "Adobe Commerce on-premise 2.4.2: immagine del prodotto mancante"
description: Questo articolo descrive un problema noto di Adobe Commerce on-premise 2.4.2 in cui l’immagine del prodotto non viene caricata nella pagina del prodotto. Questo problema è pianificato per essere risolto in una versione futura dopo la versione 2.4.3. Al momento non è disponibile una soluzione, ma come soluzione alternativa puoi disabilitare Nginx per ridimensionare le immagini.
exl-id: c4d9240e-5df5-4eab-bb4e-1f06f9bd3a1e
feature: Iaas, Products, Storefront
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# Adobe Commerce on-premise 2.4.2: immagine del prodotto mancante

Questo articolo descrive un problema noto di Adobe Commerce on-premise 2.4.2 in cui l’immagine del prodotto non viene caricata nella pagina del prodotto. Questo problema è pianificato per essere risolto in una versione futura dopo la versione 2.4.3. Al momento non è disponibile una soluzione, ma come soluzione alternativa puoi disabilitare Nginx per ridimensionare le immagini.

## Prodotti e versioni interessati

* Adobe Commerce on-premise 2.4.2

## Problema

L’immagine del prodotto viene salvata in `s3` bucket, ma non viene sincronizzato di nuovo nel `pub/media` directory. Questo problema si verifica solo quando si utilizzano entrambi:

* Nginx abilitato per il sito per ridimensionare le immagini
* AWS `s3` come storage multimediale

<u>Prerequisiti</u>:

Adobe Commerce installato con Nginx.

<u>Passaggi da riprodurre</u>:

1. Configurare Adobe Commerce per l’utilizzo di AWS `s3` come storage multimediale.
1. Configurare Nginx utilizzando `nginx.conf.sample` file di configurazione fornito nella directory di installazione di Adobe Commerce e in un host virtuale Nginx. Consulta [Configurare Nginx](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/nginx.html#configure-nginx-ubuntu) nella documentazione per gli sviluppatori.
1. Crea un prodotto semplice con un’immagine del prodotto.
1. Nginx ha una configurazione senza commenti per il ridimensionamento delle immagini in `nginx.conf.sample` simile a questo:

```conf
load_module /etc/nginx/modules/ngx_http_image_filter_module.so;
location /media/ {
    location ~* ^/media/catalog/.* {
        set $width "-";
        set $height "-";
        if ($arg_width != '') {
            set $width $arg_width;
        }
        if ($arg_height != '') {
            set $height $arg_height;
        }
        image_filter resize $width $height;
        image_filter_jpeg_quality 90;
    }
```

<u>Risultati previsti</u>:

L’immagine del prodotto viene caricata nella pagina del prodotto.

<u>Risultati effettivi</u>:

L’immagine del prodotto non viene caricata nella pagina del prodotto.

## Soluzione alternativa

Disattiva Nginx per ridimensionare le immagini.
