---
title: "MBI: nuova autenticazione delle integrazioni"
description: Questo articolo fornisce soluzioni per autorizzare nuovamente un’integrazione al fine di concedere al Magento Business Intelligence (MBI) i privilegi necessari per estrarre dati da un servizio di terze parti. Quando questi privilegi vengono revocati, è necessaria una nuova autorizzazione.
exl-id: c608d6f9-64a5-44f8-9d7b-9a85a2668775
feature: Commerce Intelligence, Integration
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# MBI: nuova autenticazione delle integrazioni

Questo articolo fornisce soluzioni per autorizzare nuovamente un’integrazione al fine di concedere al Magento Business Intelligence (MBI) i privilegi necessari per estrarre dati da un servizio di terze parti. Quando questi privilegi vengono revocati, è necessaria una nuova autorizzazione.

## Integrazioni di database e SaaS

Per gli elenchi delle integrazioni di Database e SaaS, fare riferimento a [Connessione di dati esterni tramite un’integrazione](https://docs.magento.com/mbi/data-analyst/importing-data/integrations/integrations.html) nella documentazione per gli sviluppatori. All’apertura della pagina, utilizza il sommario a sinistra per la navigazione.

## Problemi di connessione?

L’autorizzazione di un’integrazione concede a MBI i privilegi necessari per estrarre i dati da un servizio di terze parti. Quando questi privilegi vengono revocati, è necessaria una nuova autorizzazione.

Ciò potrebbe verificarsi per una serie di motivi:

* un problema con il servizio di terze parti
* scadenza token di autenticazione
* una modifica apportata al tuo account amministrativo
* o un problema interno in MBI

Lo stato di tutte le integrazioni si trova nella pagina Integrazioni ( **Gestisci dati > Integrazioni** ):

![Integrazioni_page.png](assets/Integrations_page.png)

Per autenticare di nuovo, potrebbe essere necessario immettere nuovamente le credenziali dell&#39;account. In alcuni casi, potrebbe essere necessario generare nuove chiavi API per l’integrazione del problema. Fai clic sul nome dell’integrazione del problema per avviare il processo di riautorizzazione.

Se il problema persiste, [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
