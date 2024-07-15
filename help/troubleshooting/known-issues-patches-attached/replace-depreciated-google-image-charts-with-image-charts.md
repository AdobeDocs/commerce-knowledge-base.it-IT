---
title: Sostituisci i grafici immagine Google obsoleti con i grafici immagine
description: La maggior parte delle edizioni e versioni di Adobe Commerce attualmente utilizza [Google Image Charts](https://developers.google.com/chart/image/) per eseguire il rendering dei grafici statici nelle dashboard di amministrazione. A partire dal 14 marzo 2019, Google cesserà di supportare i grafici a immagini Google. Per risolvere questo problema, forniamo una patch per sostituire Google Image Charts con il servizio gratuito [Image-Charts](https://www.image-charts.com/).
exl-id: f86f0bb9-8a03-471d-8696-1eba4b8acbd1
feature: Cache, Compliance
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 0%

---

# Sostituisci i grafici immagine Google obsoleti con i grafici immagine

La maggior parte delle edizioni e versioni di Adobe Commerce attualmente utilizzano [grafici immagine Google](https://developers.google.com/chart/image/) per eseguire il rendering di grafici statici nei dashboard di amministrazione. A partire dal 14 marzo 2019, Google cesserà di supportare i grafici a immagini Google. Per risolvere questo problema, stiamo fornendo una patch per sostituire Google Image Charts con il servizio gratuito [Image-Charts](https://www.image-charts.com/).

## Versioni interessate

* Adobe Commerce 1.X, tutte le edizioni
* Adobe Commerce 2.X, tutte le edizioni

>[!NOTE]
>
>Adobe Commerce on-premise 1.14.4.1, Magento Open Source 1.9.4.1, Adobe Commerce on-premise e Adobe Commerce on cloud infrastructure 2.3.2 includeranno questo aggiornamento del grafico. L’aggiornamento a queste versioni continua a supportare i grafici a immagini senza patch aggiuntive.

## Problema

Google ha smesso di supportare Google Image Charts il 14 marzo 2019. Gli utenti di Adobe Commerce 1.X e Adobe Commerce 2.2.X di tutte le versioni non potranno visualizzare i grafici statici a meno che non scarichino e applichino la patch, sostituendo Google Image Charts con la soluzione Image-Charts. I grafici visualizzati avranno la stessa struttura e funzionalità dei grafici immagine di Google tramite il servizio di account gratuito Image-Charts con l&#39;informativa sulla privacy di conformità [GDPR](https://www.image-charts.com/data-processing-addendum.html). Per ulteriori opzioni, vedere [Grafici immagine](https://www.image-charts.com/).

## Soluzione

Per visualizzare i grafici statici in Commerce Admin, scarica e applica la patch fornita da Adobe Commerce. Non sono necessarie configurazioni aggiuntive.

### Adobe Commerce on-premise

1. Salva la patch [collegata MAGETWO-98833\_compositore\_patch-2019-04-15-04-38-57.patch](assets/MAGETWO-98833_composer_patch-2019-04-15-04-38-57.patch.zip) e caricala nella directory principale di Adobe Commerce.
1. Esegui il seguente comando SSH, dopo aver sostituito il nome della patch con quello effettivo:

   ```git
   patch -p1 < MAGETWO-98833_composer_patch-2019-04-15-04-38-57.patch
   ```

   Se il comando precedente non funziona, provare a utilizzare `-p2` anziché `-p1`.)

1. Affinché le modifiche vengano applicate, aggiorna la cache nell&#39;amministratore in **Sistema** > **Gestione cache**.

### Adobe Commerce sull’infrastruttura cloud

Per i commercianti di Cloud, la patch verrà inclusa nell’aggiornamento ECE-tools più vicino.

### Magento 2 Open Source

1. Vai a [https://magento.com/tech-resources/download\#download2291](https://magento.com/tech-resources/download#download2291).
1. Nell&#39;elenco a discesa **Seleziona il formato**, seleziona la versione del compositore e fai clic su **Scarica**.
1. Carica la patch nella directory principale di Adobe Commerce.
1. Esegui il seguente comando SSH, dopo aver sostituito il nome della patch con quello effettivo:

   ```git
   patch -p1 < MAGETWO-98833_composer_patch-2019-04-15-04-37-48.patch
   ```

   Se il comando precedente non funziona, provare a utilizzare `-p2` anziché `-p1`.

1. Affinché le modifiche vengano applicate, aggiorna la cache nell&#39;amministratore in **Sistema** > **Gestione cache**.

### Adobe Commerce 1 on-premise

Per scaricare e applicare la patch, segui la procedura riportata di seguito:

1. Salva la patch [allegata MPERF-10509-EE-2019-03-13-06-32-19.diff](assets/MPERF-10509-EE-2019-03-13-06-32-19.diff.zip) e caricala nella directory principale di Adobe Commerce.
1. Esegui il seguente comando SSH:

   ```git
   patch -p1 < MPERF-10509-EE-2019-03-13-06-32-19.diff
   ```

   Se il comando precedente non funziona, provare a utilizzare `-p2` anziché `-p1`.

1. Affinché le modifiche vengano applicate, aggiorna la cache nell&#39;amministratore in **Sistema** > **Gestione cache**.

### Magento 1 Open Source

Per scaricare e applicare la patch, segui la procedura riportata di seguito:

1. Fai clic su [**questo collegamento**](https://magento.com/tech-resources/download#download2283) per individuare la patch dei grafici del dashboard di amministrazione.
1. Seleziona

   ```git
   MPERF-10509.diff
   ```

   Dal menu a discesa **Seleziona il formato** e fai clic su Scarica.

1. Carica il file nella directory principale di Adobe Commerce.
1. Esegui il seguente comando SSH:

   ```git
   patch -p1 < MPERF-10509.diff
   ```

   Se il comando precedente non funziona, provare a utilizzare `-p2` anziché `-p1`.

1. Affinché le modifiche vengano applicate, aggiorna la cache nell&#39;amministratore in **Sistema** > **Gestione cache**.

## File allegati

[Scarica MAGETWO-98833_compositore_patch-2019-04-15-04-38-57.patch](assets/MAGETWO-98833_composer_patch-2019-04-15-04-38-57.patch)

[Scarica MPERF-10509-EE-2019-03-13-06-32-19.diffh](assets/MPERF-10509-EE-2019-03-13-06-32-19.diff)
