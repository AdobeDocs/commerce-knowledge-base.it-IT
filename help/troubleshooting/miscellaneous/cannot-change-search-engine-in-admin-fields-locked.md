---
title: Impossibile cambiare il motore di ricerca in "app/etc/env.php"
description: Questo articolo fornisce una soluzione al problema per cui si tenta di modificare il motore di ricerca nell’amministratore di Commerce, ma i campi sono bloccati.
exl-id: 61006ce7-34f9-4e4d-a197-f3d627dd277f
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# Impossibile modificare il motore di ricerca in `app/etc/env.php`

Questo articolo fornisce una soluzione al problema relativo alla rimozione della configurazione del motore di ricerca dal `app/etc/env.php` ma dopo la ridistribuzione, la configurazione torna all’impostazione precedente o viene modificata in [!DNL OpenSearch] per impostazione predefinita.

## Prodotti e versioni interessati

* Adobe Commerce sull’infrastruttura cloud, [tutte le versioni supportate](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problema

Si tenta di cambiare il motore di ricerca nell&#39;amministratore di Commerce, ma i campi sono bloccati.

## Causa

La configurazione del motore di ricerca è bloccata in `app/etc/env.php` o il motore di ricerca è definito in modo esplicito nel file `.magento.env.yaml` file.

## Soluzione

1. Controlla la `.magento.env.yaml` nella fase di distribuzione e verifica se `SEARCH_CONFIGURATION` è stata configurata. Esempio:

   ```yaml
   SEARCH_CONFIGURATION:
     engine: elasticsearch7
     ...
   <VARIABLE X>
   ```

1. È il  `SEARCH_CONFIGURATION` variabile presente? Se non presente, la configurazione del motore di ricerca è bloccata su [!DNL OpenSearch] per impostazione predefinita. Per modificare la configurazione, devi aggiungere la variabile alla `.magento.env.yaml` con il valore appropriato per il motore di ricerca. Se il `SEARCH_CONFIGURATION` è presente e desideri modificare il motore, sostituisci il valore esistente per il motore in `.magento.env.yaml`. Valori possibili/noti: [!DNL opensearch], [!DNL livesearch], [!DNL elasticsuite], [!DNL amasty_elastic], e [!DNL amasty_elastic_opensearch].
1. Ridistribuisci l’istanza.
1. Il campo del motore di ricerca nell’Amministratore rimarrà bloccato, ma dovrebbe essere aggiornato con il valore specificato.

## Lettura correlata

* [Campi bloccati in Amministrazione Commerce](/help/troubleshooting/miscellaneous/locked-fields-in-magento-admin.md) nella Guida all’infrastruttura cloud di Commerce.
