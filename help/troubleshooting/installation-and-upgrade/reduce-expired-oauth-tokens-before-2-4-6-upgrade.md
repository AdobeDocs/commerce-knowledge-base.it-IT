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

# Riduci scaduti `oauth_tokens` prima dell’aggiornamento 2.4.6

Questo articolo fornisce una soluzione al problema in cui è presente un numero elevato di `oauth_tokens` nel tuo `oauth_token` che può causare un lungo ritardo nell’aggiornamento alla versione 2.4.6. Si consiglia di ridurre il `oauth_token` tabella che utilizza [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] processo per eliminare i token scaduti.

## Prodotti e versioni interessati

* Adobe Commerce 2.4.0 - 2.4.6, tutti i metodi di implementazione

## Problema

Se il numero di `oauth_tokens` nel tuo `oauth_token` che può causare un lungo ritardo nell’aggiornamento alla versione 2.4.6.

Il processo di aggiornamento include la crittografia di tali token per un ulteriore livello di sicurezza ed è stato eseguito solo 100 record alla volta. Se il numero di token è elevato, l’operazione potrebbe richiedere diverse ore.

Riduzione di un numero elevato di `oauth_tokens` nel tuo `oauth_token` Questa tabella può evitare un lungo ritardo nell’aggiornamento alla versione 2.4.6.

## Soluzione

Prima di avviare un aggiornamento, assicurati che il [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] processo in esecuzione. Riduce le dimensioni del `oauth_token` tabella eliminando i valori scaduti `oauth_tokens` token e devono essere già abilitati per impostazione predefinita.

Per attivare manualmente [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] job, esegui:
```bin/magento cron:run --group=default```

## Lettura correlata

* [Servizi > [!DNL OAuth]](https://experienceleague.adobe.com/docs/commerce-admin/config/services/oauth.html) nella guida di riferimento alla configurazione di Commerce.
* [Guida all’autenticazione](https://developer.adobe.com/developer-console/docs/guides/authentication/) nella guida di Adobe Developer.
