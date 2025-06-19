---
title: Impossibile cambiare il motore di ricerca in "app/etc/env.php"
description: Questo articolo fornisce una soluzione al problema per cui si tenta di modificare il motore di ricerca nell’amministratore di Commerce, ma i campi sono bloccati.
exl-id: 61006ce7-34f9-4e4d-a197-f3d627dd277f
source-git-commit: 129e24366aedb132adb84e1f0196d2536422180f
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---

# Impossibile modificare il motore di ricerca in `app/etc/env.php`

In questo articolo viene fornita una soluzione al problema in cui si tenta di rimuovere la configurazione del motore di ricerca dal file `app/etc/env.php`, ma dopo la ridistribuzione la configurazione torna all&#39;impostazione precedente o viene modificata in [!DNL OpenSearch] per impostazione predefinita.

## Prodotti e versioni interessati

* Adobe Commerce sull&#39;infrastruttura cloud, [tutte le versioni supportate](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problema

Si tenta di cambiare il motore di ricerca nell&#39;amministratore di Commerce, ma i campi sono bloccati.

## Causa

La configurazione del motore di ricerca è bloccata nel file `app/etc/env.php` oppure il motore di ricerca è definito in modo esplicito nel file `.magento.env.yaml`.

## Soluzione

1. Controllare il file `.magento.env.yaml` nella fase di distribuzione e verificare se la variabile `SEARCH_CONFIGURATION` è stata configurata. Esempio:

   ```yaml
   SEARCH_CONFIGURATION:
     engine: elasticsearch7
     ...
   <VARIABLE X>
   ```

1. La variabile `SEARCH_CONFIGURATION` è presente? Se non presente, la configurazione del motore di ricerca è bloccata su [!DNL OpenSearch] per impostazione predefinita. Per modificare la configurazione, aggiungere la variabile al file `.magento.env.yaml` con il valore appropriato per il motore di ricerca. Se la variabile `SEARCH_CONFIGURATION` è presente e si desidera modificare il motore, sostituire il valore esistente per il motore in `.magento.env.yaml`. Valori possibili/noti: [!DNL opensearch], [!DNL livesearch], [!DNL elasticsuite], [!DNL amasty_elastic] e [!DNL amasty_elastic_opensearch].
1. Ridistribuisci l’istanza.
1. Il campo del motore di ricerca nell’Amministratore rimarrà bloccato, ma dovrebbe essere aggiornato con il valore specificato.

## Lettura correlata

* [Campi bloccati (disattivati) in Commerce Admin](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26879) nella Guida di Commerce on Cloud Infrastructure.
