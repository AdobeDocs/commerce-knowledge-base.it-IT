---
title: Errore durante la convalida delle credenziali Fastly
description: Questo articolo fornisce una soluzione per il problema in cui un utente riceve un errore durante la convalida delle credenziali Fastly.
exl-id: 02104731-6666-47a6-abc6-215812f09915
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# Errore durante la convalida delle credenziali Fastly

Questo articolo fornisce una soluzione per il problema in cui un utente riceve un errore durante la convalida delle credenziali Fastly.

## Problema

L’utente riceve un errore durante la convalida delle credenziali Fastly.

## Prodotti e versioni interessati

* Adobe Commerce (tutti i metodi di distribuzione): tutte le versioni
* Estensione o versione della tecnologia (Fastly, New Relic, ecc.) Fastly

## Soluzione

1. Verifica di disporre dell’ID servizio Fastly e del token API corretti, quindi riprova a eseguire la convalida. Per istruzioni dettagliate, consulta [Verifica le credenziali Fastly](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#test-the-fastly-credentials) nella documentazione per gli sviluppatori.
1. Se la verifica delle credenziali non riesce, esegui il seguente comando curl per confermare lo stato del servizio:

   ```curl
   curl -H "Fastly-Key: <API key>" https://api.fastly.com/service/<service ID>/version/active
   ```

1. Se il comando precedente restituisce un errore simile al seguente: *{&quot;msg&quot;:&quot;Token $TOKEN scaduto il 2021-09-28T02:03:37Z&quot;}*, invia un ticket di supporto per richiedere un nuovo token API.

   Per informazioni su come inviare un ticket di supporto, consulta [Guida utente del Centro assistenza Adobe Commerce > TICKET DI SUPPORTO](/help/help-center-guide/help-center/magento-help-center-user-guide.md#support-tickets) nella nostra knowledge base di supporto.

   >[!NOTE]
   >
   >Non condividere mai password o token API validi/attivi direttamente nel ticket, poiché per motivi di sicurezza dovremo revocare il token corrente e generarne uno nuovo.

1. Se il comando non restituisce l&#39;errore, verificare di eseguire la versione più recente dell&#39;estensione [!DNL Fastly]. Se utilizzi una versione precedente alla 1.2.203, devi fare clic su **[!UICONTROL Save Config]** prima di poter verificare le credenziali.

## Letture correlate nella documentazione per gli sviluppatori:

* [Cloud per Adobe Commerce > Fastly > Account e credenziali del servizio Fastly](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/cdn/fastly#fastly-service-account-and-credentials)

* [Cloud per Adobe Commerce > Configura velocemente > Verifica le credenziali Fastly](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#test-the-fastly-credentials)
