---
title: robots.txt non aggiornato o non visualizza le impostazioni predefinite
description: L’articolo fornisce una soluzione per quando hai configurato correttamente "robots.txt", ad esempio per [Best practice per Adobe Commerce robots.txt](https://support.magento.com/hc/en-us/articles/360048754931) ma "robots.txt" non viene aggiornato o visualizza le impostazioni predefinite.
exl-id: 629b1247-9282-49f9-ada3-a804ddbaa0f5
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---

# robots.txt non aggiornato o non visualizza le impostazioni predefinite

L&#39;articolo fornisce una soluzione per quando `robots.txt` è stato configurato correttamente, ad esempio per [Best practice per Adobe Commerce robots.txt](https://support.magento.com/hc/en-us/articles/360048754931), ma `robots.txt` non viene aggiornato o visualizza le impostazioni predefinite.

## Prodotti e versioni interessati

* Adobe Commerce sull’infrastruttura cloud 2.3.x, 2.4.x

## Problema

Impossibile modificare l&#39;impostazione predefinita `robots.txt`.

<u>Passaggi da riprodurre:</u>

1. Accedi al pannello Amministratore.
1. Aggiungi contenuto a **Contenuto** > Progettazione > **Configurazione** > **Modifica istruzione personalizzata del file`robots.txt`**, ad esempio il testo &quot;hello&quot; e salva le modifiche.
1. Visita l&#39;URL `robots.txt`.

<u>Risultato previsto:</u>
`robots.txt` ha il testo salvato.

<u>Risultato effettivo:</u>

Il file `robots.txt` non cambia.

## Causa

L&#39;indicizzazione da parte dei motori di ricerca è disattivata.

## Soluzione

Abilita l’indicizzazione tramite i motori di ricerca. Consulta [Configurare l&#39;indicizzazione tramite il motore di ricerca](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap#configure-indexing-by-search-engine) nella documentazione per gli sviluppatori.

## Lettura correlata

* [Aggiungi mappa del sito e robot motore di ricerca](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap) nella documentazione per gli sviluppatori.
