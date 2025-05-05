---
title: 'Patch riviste per Google Maps: perdita di accesso su tutte le versioni di Adobe Commerce'
description: 'Questo articolo fornisce una correzione per gli esercenti di Adobe Commerce che non sono compatibili con nessuna versione recente di [!DNL Google Maps] dalla versione 3.54+.'
feature: Install, Upgrade
role: Developer
source-git-commit: cf235c2fdd7a36d7e3b126de35c51e6711cd3845
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# Patch riviste per la perdita dell&#39;accesso [!DNL Google Maps] su tutte le versioni di Adobe Commerce

Questo articolo fornisce una correzione per gli esercenti Adobe Commerce che non sono compatibili con nessuna versione [!DNL Google Maps] recente dalla versione 3.54+. Questa correzione consente di risolvere il problema per cui i commercianti di Adobe Commerce non hanno più accesso a [!DNL Google Maps] in alcuna versione di Adobe Commerce.

## Versioni e prodotti interessati

* Versioni di Adobe Commerce e/o altre tecnologie utilizzate.
* Adobe Commerce *2.4.4* - *2.4.7* nelle versioni Cloud e On-Premise.

## Problema

Il *14 giugno 2024* la versione [!DNL Google Maps] *3.53* ha raggiunto la fine del ciclo di vita ed è stata disattivata da [!DNL Google].

Per ulteriori informazioni, fare riferimento a [[!DNL Google Maps Platform: Maps JavaScript API]](https://developers.google.com/maps/documentation/javascript/versions#documentation-for-the-api-versions).

Adobe Commerce non è compatibile con nessuna versione [!DNL &#x200B; Google Maps] recente dalla versione 3.54+.

L&#39;incompatibilità è stata causata dalla versione legacy di `prototype.js script`, caricata tramite `lib/web/legacy-build.min.js`, che sostituisce la funzione nativa Array.from, causando un conflitto diretto con l&#39;API [!DNL &#x200B; Google Maps].

Fare riferimento a [[!DNL Google Maps: JS Best Practices]](https://developers.google.com/maps/documentation/javascript/best-practices).

<u>Passaggi da riprodurre</u>:

1. Fai clic su **[!UICONTROL Content]** > **[!UICONTROL Pages]** > e seleziona un **[!UICONTROL New Page]**.
1. Espandere il blocco di contenuto e fare clic sul pulsante Modifica **[!DNL PageBuilder]**.
1. Trascinare il Blocco di contenuto mappa dal menu **[!DNL PageBuilder]** nella pagina.

<u>Risultato previsto:</u>

[!DNL Google Maps] dovrebbe funzionare come previsto.

<u> Risultato effettivo:</u>

Quando si rilascia il Blocco di contenuto della mappa dal menu **[!DNL PageBuilder]** alla pagina, viene visualizzato un messaggio di errore come *&quot;Spiacenti! Si è verificato un errore&quot;* visualizzato.

## Soluzione

* Tutti i commercianti di qualsiasi versione delle patch 2.4.4, 2.4.5, 2.4.6 o 2.4.7 devono applicare le patch corrispondenti alla propria versione.

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

Questo problema verrà risolto definitivamente nell’ambito delle versioni di patch di sicurezza di agosto:
2.4.7-p2, 2.4.6-p7, 2.4.5-p9, 2.4.4-p10

## Lettura correlata

[Applicare una patch del compositore fornita dall&#39;Adobe](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento)