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

Questo articolo corregge quando `robots.txt` Il file genera un errore 404 in Adobe Commerce sull’infrastruttura cloud.

## Prodotti e versioni interessati

Adobe Commerce su infrastruttura cloud (tutte le versioni)

## Problema

Il `robots.txt` il file non funziona e genera un&#39;eccezione Nginx. Il `robots.txt` viene generato dinamicamente &quot;al volo&quot;. Il `robots.txt` il file non è accessibile da `/robots.txt` URL perché Nginx ha una regola di riscrittura che reindirizza forzatamente tutti `/robots.txt` richieste a `/media/robots.txt` che non esiste.

## Causa

Ciò si verifica in genere quando Nginx non è configurato correttamente.

## Soluzione

La soluzione consiste nel disattivare la regola Nginx che reindirizza `/robots.txt` richieste a `/media/robots.txt` file. I commercianti con il self-service abilitato possono farlo da soli e i commercianti senza il self-service abilitato devono creare un ticket di supporto.

Se il self-service non è abilitato (o non si è sicuri se è abilitato), [invia un ticket di supporto Magento](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) richiesta di rimozione della regola di reindirizzamento Nginx da `/robots.txt` richieste a `/media/robots.txt`.

Se il self-service è abilitato, aggiornare ECE-Tools ad almeno 2002.0.12 e rimuovere la regola di reindirizzamento Nginx nel `.magento.app.yaml` file. Puoi consultare [Aggiungi mappa del sito e robot per motori di ricerca](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap.html) per ulteriori informazioni, consulta la documentazione per gli sviluppatori.

## Lettura correlata

* [Come bloccare il traffico dannoso per il Magento Commerce Cloud a livello Fastly](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) nella nostra knowledge base di supporto.
* [Aggiungi mappa del sito e robot per motori di ricerca](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html) nella documentazione per gli sviluppatori.
* [Robot motore di ricerca](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots) nella guida utente.
