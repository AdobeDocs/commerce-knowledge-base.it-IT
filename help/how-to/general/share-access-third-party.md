---
title: Suggerimenti per i test di terze parti per Adobe Commerce sull’infrastruttura cloud
description: Questo articolo fornisce opzioni per condividere l’accesso con terze parti a scopo di test/convalida in caso di problemi con un’estensione per Adobe Commerce sull’infrastruttura cloud.
exl-id: e2d80aa9-8b68-48ed-bec5-68e128611a1e
feature: Best Practices, Cloud
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# Suggerimenti per i test di terze parti per Adobe Commerce sull’infrastruttura cloud

Questo articolo fornisce opzioni per condividere l’accesso con terze parti a scopo di test/convalida in caso di problemi con un’estensione per Adobe Commerce sull’infrastruttura cloud.
Quando decidi come fornire l’accesso a terzi, devi seguire le procedure e i requisiti interni di sicurezza dei dati.

## Prodotti e versioni interessati:

* Adobe Commerce su infrastruttura cloud 2.3.0 - 2.3.7-p1, 2.4.0 - 2.4.3

## Quali ambienti utilizzare per il test

A seconda degli standard di sicurezza interni, è possibile scegliere di eseguire la risoluzione dei problemi di terze parti in un ambiente locale. Se il problema non può essere riprodotto localmente, è possibile fornire l’accesso all’ambiente cloud. Se decidi di farlo, assicurati di agire nel rispetto degli standard di sicurezza interni. Se fornisci l’accesso a uno qualsiasi degli ambienti cloud, assicurati che le terze parti sappiano chiaramente cosa è possibile fare e quale approvazione è necessaria per attività quali la sola replica o l’autorizzazione di modifiche al codice. Questo è particolarmente importante per gli ambienti di produzione.

## Fornire a terzi accesso e dati

* Fornisci l’accesso di fornitori terzi all’ambiente cloud. Articoli correlati:

   * [Guida utente di Adobe Commerce Help Center > ACCESSO CONDIVISO: CONCEDI PRIVILEGI AD ALTRI UTENTI PER ACCEDERE AL TUO ACCOUNT](/help/help-center-guide/help-center/magento-help-center-user-guide.md#shared-access) nella nostra Knowledge Base di supporto.
   * [Condivisione dell&#39;account Commerce](https://docs.magento.com/user-guide/magento/magento-account-share.html) nella guida utente.

* Crea un’immagine del database (o concedi al fornitore di terze parti l’accesso per farlo). Può essere eseguita utilizzando CLI o in Commerce Admin. Questo dump del database offuscherà i dati dei clienti, quindi tutto ciò che ottengono è codice e SKU del prodotto, ecc., nessun dato proprietario/cliente. Per riferimento, utilizzare [Condivisione dell&#39;account Commerce] (/help/how-to/general/create-database-dump-on-cloud.md) nella Knowledge Base di supporto.
* Una volta completato il test, assicurati di revocare l&#39;accesso condiviso all&#39;ambiente cloud, come descritto in [Guida utente di Adobe Commerce Help Center > Revoca (elimina l&#39;accesso condiviso)](/help/help-center-guide/help-center/magento-help-center-user-guide.md#revoke-shared-access) nella nostra knowledge base di supporto.

## Best practice per la verifica

La procedura standard prevede la risoluzione dei problemi in un ambiente locale. Se il problema non può essere riprodotto localmente, passa a Staging. La terza parte potrebbe dover controllare la produzione. Assicurati che le terze parti siano a conoscenza del fatto che devono solo tentare di riprodurre il problema in Produzione e staging e di non apportare modifiche al codice. Se devono apportare modifiche al codice, devono prima ottenere l’autorizzazione.

## Lettura correlata

* [Procedure consigliate per l&#39;utilizzo di estensioni di terze parti in Adobe Commerce](https://support.magento.com/hc/en-us/articles/360042361152-Best-Practices-for-using-third-party-extensions-in-Magento) nella Knowledge Base di supporto.
