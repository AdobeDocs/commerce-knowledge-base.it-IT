---
title: robots.txt restituisce l’errore 404 Adobe Commerce sull’infrastruttura cloud
description: Questo articolo fornisce una correzione per quando il file "robots.txt" genera un errore 404 in Adobe Commerce sull’infrastruttura cloud.
exl-id: 6f0b9f47-1901-4c43-88d8-fd992015d70f
feature: Cloud, Marketing Tools, Paas
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# robots.txt restituisce l’errore 404 Adobe Commerce sull’infrastruttura cloud

Questo articolo fornisce una correzione per quando il file `robots.txt` genera un errore 404 in Adobe Commerce sull&#39;infrastruttura cloud.

## Prodotti e versioni interessati

Adobe Commerce su infrastruttura cloud (tutte le versioni)

## Problema

Il file `robots.txt` non funziona e genera un&#39;eccezione Nginx. Il file `robots.txt` viene generato dinamicamente &quot;al volo&quot;. Il file `robots.txt` non è accessibile dall&#39;URL `/robots.txt` perché Nginx dispone di una regola di riscrittura che reindirizza forzatamente tutte le richieste `/robots.txt` al file `/media/robots.txt` che non esiste.

## Causa

Ciò si verifica in genere quando Nginx non è configurato correttamente.

## Soluzione

La soluzione consiste nel disabilitare la regola Nginx che reindirizza `/robots.txt` richieste al file `/media/robots.txt`. I commercianti con il self-service abilitato possono farlo da soli e i commercianti senza il self-service abilitato devono creare un ticket di supporto.

Se il self-service non è abilitato (o non si è sicuri se è abilitato), [invia un ticket di supporto di Magento](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) richiedendo la rimozione della regola di reindirizzamento Nginx da `/robots.txt` richieste a `/media/robots.txt`.

Se il self-service è abilitato, aggiornare ECE-Tools almeno alla versione 2002.0.12 e rimuovere la regola di reindirizzamento Nginx nel file `.magento.app.yaml`. Per ulteriori informazioni, consulta [Aggiungere una mappa del sito e i robot dei motori di ricerca](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap.html) nella documentazione per gli sviluppatori.

## Lettura correlata

* [Come bloccare il traffico dannoso per il Magento Commerce Cloud al livello Fastly](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) nella Knowledge Base di supporto.
* [Aggiungi mappa del sito e robot motore di ricerca](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html) nella documentazione per gli sviluppatori.
* [Robot per motori di ricerca](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots) nella guida utente.
