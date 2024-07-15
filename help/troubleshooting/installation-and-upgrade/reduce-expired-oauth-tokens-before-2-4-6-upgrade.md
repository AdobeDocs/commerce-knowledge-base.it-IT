---
title: Riduci i "oauth_tokens" scaduti prima dell’aggiornamento alla versione 2.4.6
description: Questo articolo fornisce una soluzione al problema per cui visualizzi un numero elevato di "oauth_tokens" nella tabella "oauth_token", che può causare un lungo ritardo nell’aggiornamento alla versione 2.4.6. Si consiglia di ridurre la tabella "oauth_token" utilizzando CleanExpiredTokens.php.
feature: Variables, Upgrade
role: Developer
exl-id: 92d1d15a-04da-4ba4-b6b8-5c491af9c4c1
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---

# Riduci `oauth_tokens` scaduto prima dell&#39;aggiornamento alla versione 2.4.6

Questo articolo fornisce una soluzione al problema che causa la visualizzazione di un numero elevato di `oauth_tokens` nella tabella `oauth_token`, che può causare un ritardo prolungato nell&#39;aggiornamento alla versione 2.4.6. È consigliabile ridurre la tabella `oauth_token` utilizzando il processo [!DNL cron] [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) per eliminare i token scaduti.

## Prodotti e versioni interessati

* Adobe Commerce 2.4.0 - 2.4.6, tutti i metodi di implementazione

## Problema

Se nella tabella `oauth_token` è presente un numero elevato di `oauth_tokens`, l&#39;aggiornamento alla versione 2.4.6 potrebbe subire un lungo ritardo.

Il processo di aggiornamento include la crittografia di tali token per un ulteriore livello di sicurezza ed è stato eseguito solo 100 record alla volta. Se il numero di token è elevato, l’operazione potrebbe richiedere diverse ore.

La riduzione di un numero elevato di `oauth_tokens` nella tabella `oauth_token` può evitare un ritardo prolungato nell&#39;aggiornamento alla versione 2.4.6.

## Soluzione

Prima di avviare un aggiornamento, verificare che il processo [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] sia in esecuzione. Riduce le dimensioni della tabella `oauth_token` eliminando i token `oauth_tokens` scaduti e dovrebbe essere già abilitato per impostazione predefinita.

Per attivare manualmente il processo [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron], eseguire:
```bin/magento cron:run --group=default```

## Lettura correlata

* [Servizi > [!DNL OAuth]](https://experienceleague.adobe.com/docs/commerce-admin/config/services/oauth.html) nella guida di riferimento alla configurazione di Commerce.
* [Guida all&#39;autenticazione](https://developer.adobe.com/developer-console/docs/guides/authentication/) nella guida di Adobe Developer.
