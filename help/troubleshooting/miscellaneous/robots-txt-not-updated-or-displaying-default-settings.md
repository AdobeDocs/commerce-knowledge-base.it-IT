---
title: robots.txt non aggiornato o non visualizza le impostazioni predefinite
description: L’articolo fornisce una soluzione per quando hai configurato correttamente "robots.txt", ad esempio per [Best practice per Adobe Commerce robots.txt](https://support.magento.com/hc/en-us/articles/360048754931) ma "robots.txt" non viene aggiornato o visualizza le impostazioni predefinite.
exl-id: 629b1247-9282-49f9-ada3-a804ddbaa0f5
feature: Configuration
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---

# robots.txt non aggiornato o non visualizza le impostazioni predefinite

L’articolo fornisce una soluzione per quando hai configurato `robots.txt` correttamente, ad esempio per [Best practice per Adobe Commerce robots.txt](https://support.magento.com/hc/en-us/articles/360048754931) ma il `robots.txt` non viene aggiornato o visualizza le impostazioni predefinite.

## Prodotti e versioni interessati

* Adobe Commerce sull’infrastruttura cloud 2.3.x, 2.4.x

## Problema

Impossibile modificare il valore predefinito `robots.txt` impostazione.

<u>Passaggi da riprodurre:</u>

1. Accedi al pannello Amministratore.
1. Aggiungi contenuto a **Contenuto** > Design **Configurazione** > **Modifica istruzione personalizzata di`robots.txt`** come il testo &quot;hello&quot; e salva le modifiche.
1. Visita il `robots.txt` url.

<u>Risultato previsto:</u>
`robots.txt` contiene il testo salvato.

<u>Risultato effettivo:</u>

`robots.txt` il file non cambia.

## Causa

L&#39;indicizzazione da parte dei motori di ricerca è disattivata.

## Soluzione

Abilita l’indicizzazione tramite i motori di ricerca. Consulta [Configurare l’indicizzazione per motore di ricerca](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html#configure-indexing-by-search-engine) nella documentazione per gli sviluppatori.

## Lettura correlata

* [Aggiungi mappa del sito e robot per motori di ricerca](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html) nella documentazione per gli sviluppatori.
