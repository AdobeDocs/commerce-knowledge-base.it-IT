---
title: 'Patch riviste per Google Maps: perdita di accesso su tutte le versioni di Adobe Commerce'
description: "Questo articolo fornisce una correzione per i commercianti di Adobe Commerce che non sono compatibili con [!DNL Google Maps] versioni da 3.54+."
feature: Install, Upgrade
role: Developer
source-git-commit: 98581cc9c251976339406f80764715096321126b
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# Patch riviste per [!DNL Google Maps] perdita di accesso su tutte le versioni di Adobe Commerce

Questo articolo fornisce una correzione per i commercianti di Adobe Commerce che non sono compatibili con alcuna [!DNL Google Maps] versioni da 3.54+. Questa correzione consente di risolvere il problema a cui i commercianti di Adobe Commerce non hanno accesso [!DNL Google Maps] in qualsiasi versione di Adobe Commerce.

## Versioni e prodotti interessati

* Versioni di Adobe Commerce e/o altre tecnologie utilizzate.
* Adobe Commerce *2.4.4.* - *2.4.7.* nelle versioni Cloud e On-Premises.

## Problema

On *14 giugno 2024* [!DNL Google Maps] version *3,53* ha raggiunto la fine del ciclo di vita ed è stato disattivato da [!DNL Google].

Per ulteriori informazioni, consulta [[!DNL Google Maps Platform: Maps JavaScript API]](https://developers.google.com/maps/documentation/javascript/versions#documentation-for-the-api-versions).

Adobe Commerce non era compatibile con nessun recente [!DNL  Google Maps] versioni da 3.54+.

L’incompatibilità è stata causata da precedenti `prototype.js script`, caricato tramite `lib/web/legacy-build.min.js` sostituisce la funzione nativa Array.from, che provoca un conflitto diretto con [!DNL  Google Maps] API.

Fai riferimento a [[!DNL Google Maps: JS Best Practices]](https://developers.google.com/maps/documentation/javascript/best-practices).

<u>Passaggi da riprodurre</u> :

1. Fai clic su **[!UICONTROL Content]** > **[!UICONTROL Pages]** > e seleziona un’ **[!UICONTROL New Page]**.
1. Espandi il blocco di contenuto e fai clic sulla modifica. **[!DNL PageBuilder]** pulsante.
1. Trascina il blocco di contenuto della mappa da **[!DNL PageBuilder]** menu alla pagina.

<u>Risultato previsto:</u>

[!DNL Google Maps] deve funzionare come previsto.

<u> Risultato effettivo:</u>

Quando si rilascia il blocco di contenuto della mappa da **[!DNL PageBuilder]** alla pagina, un messaggio di errore come *&quot;Scusa! Si è verificato un errore&quot;* viene visualizzato.

## Soluzione

* Tutti i commercianti di qualsiasi versione delle patch 2.4.4, 2.4.5, 2.4.6 o 2.2.7 devono applicare le patch corrispondenti alla propria versione.

## Patch

Utilizza le seguenti patch allegate, a seconda della versione di Adobe Commerce:

**Per le versioni 2.4.4:**
[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_poser.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**Per le versioni 2.4.5:**
[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_poser.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**Per le versioni 2.4.6:**
[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_poser.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**Per le versioni 2.4.7:**
[ACSD-60245_Google_maps_API_2.4.7_poser.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.7_composer.patch.zip)

**Nota**

Questo problema verrà risolto definitivamente nell’ambito delle versioni di agosto delle patch riservate alla sicurezza: 2.4.7-p2, 2.4.6-p7, 2.4.5-p9, 2.4.4-p10

## Lettura correlata

[Come applicare una patch del compositore fornita dall&#39;Adobe](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento)