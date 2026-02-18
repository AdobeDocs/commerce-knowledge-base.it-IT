---
title: 'Errore durante la convalida delle credenziali  [!DNL Fastly] '
description: Questo articolo fornisce una soluzione al problema che causa un errore all'utente durante la convalida delle credenziali  [!DNL Fastly] .
exl-id: 02104731-6666-47a6-abc6-215812f09915
feature: Configuration
role: Developer
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# Errore durante la convalida delle credenziali [!DNL Fastly]

Questo articolo spiega come risolvere gli errori *Token scaduto* rilevati durante la convalida delle credenziali [!DNL Fastly].

I passaggi descritti in questo articolo si applicano anche se è necessario ruotare (eseguire il ciclo) il token API [!DNL Fastly] per motivi di sicurezza. In questi casi, è necessario inviare un ticket di supporto Adobe Commerce per richiedere un nuovo token API [!DNL Fastly].

## Problema

* Errore durante la convalida delle credenziali [!DNL Fastly].
* Sospetti che il token [!DNL Fastly] sia stato compromesso, ad esempio se è stato inavvertitamente condiviso in un ticket di supporto o pubblicato in un forum pubblico.

## Prodotti e versioni interessati

* Adobe Commerce (tutti i metodi di distribuzione): tutte le versioni
* Estensione o tecnologia ([!DNL Fastly], [!DNL New Relic], ecc.) versione [!DNL Fastly]

## Soluzione

1. Verifica di disporre dell&#39;ID servizio [!DNL Fastly] e del token API corretti e riprova a eseguire la convalida. Per istruzioni dettagliate, consulta [Verifica le [!DNL Fastly] credenziali](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration?lang=en#test-the-fastly-credentials) nella documentazione per gli sviluppatori.
1. Se la verifica delle credenziali non riesce, esegui il seguente comando curl per confermare lo stato del servizio:

   ```curl
   curl -H "Fastly-Key: <API key>" https://api.fastly.com/service/<service ID>/version/active
   ```

1. Se il comando precedente restituisce un errore simile a: `{"msg":"Token $TOKEN expired at 2021-09-28T02:03:37Z"}`, invia un ticket di supporto per richiedere un nuovo token API. Dopo aver ricevuto il nuovo token, aggiorna la configurazione nell’ambiente.

   Per informazioni su come inviare un ticket di supporto, consulta [Guida utente del Centro assistenza Adobe Commerce > TICKET DI SUPPORTO](https://experienceleague.adobe.com/it/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#support-tickets) nella nostra knowledge base di supporto.

   >[!NOTE]
   >
   >Non condividere mai password o token API validi/attivi direttamente nel ticket, poiché per motivi di sicurezza dovremo revocare il token corrente e generarne uno nuovo.
   >
   >Il supporto Adobe Commerce ha accesso ai token, pertanto non è necessario includere queste informazioni nel ticket.

1. Se il comando non restituisce l&#39;errore, verificare di eseguire la versione più recente dell&#39;estensione [!DNL Fastly]. Se utilizzi una versione precedente alla 1.2.203, devi fare clic su **[!UICONTROL Save Config]** prima di poter verificare le credenziali.

## Letture correlate nella documentazione per gli sviluppatori:

* [Cloud per Adobe Commerce > [!DNL Fastly] > [!DNL Fastly] account del servizio e credenziali](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/cdn/fastly?lang=en#fastly-service-account-and-credentials)

* [Cloud for Adobe Commerce > Configura [!DNL Fastly] > Verifica le [!DNL Fastly] credenziali](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration?lang=en#test-the-fastly-credentials)
