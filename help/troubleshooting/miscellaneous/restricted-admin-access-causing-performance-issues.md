---
title: Accesso amministratore limitato che causa problemi di prestazioni
description: Questo articolo fornisce soluzioni per i casi in cui le prestazioni sono influenzate negativamente dall’utilizzo di [Ruoli amministratore con ambito ruolo limitato dal sito web](https://docs.magento.com/m2/ee/user_guide/system/permissions-user-roles.html#step-2assign-resources) nella nostra guida utente.
exl-id: da168d6b-9cda-41e2-aa3c-f3f0dccc803d
feature: Admin Workspace, Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# Accesso amministratore limitato che causa problemi di prestazioni

Questo articolo fornisce soluzioni per i casi in cui le prestazioni sono influenzate negativamente dall&#39;utilizzo di [Ruoli amministratore con ambito ruolo limitato dal sito Web](https://docs.magento.com/m2/ee/user_guide/system/permissions-user-roles.html#step-2assign-resources) nella guida utente.

## Prodotti e versioni interessati

* Adobe Commerce on-premise 2.2.x, 2.3.x
* Adobe Commerce sull’infrastruttura cloud 2.2.x, 2.3.x

## Problema

Quando un utente amministratore, con l’ambito del ruolo limitato dal sito web, esegue operazioni nel pannello di amministrazione (tra cui accesso, salvataggio di prodotti e così via), Adobe Commerce ricostruisce la cache memorizzata. La ricostruzione della cache influisce negativamente sulle prestazioni e può causare un’interruzione del sito, soprattutto durante le ore di lavoro e/o con traffico elevato.

Il problema è risolto in Adobe Commerce 2.2.10 e 2.3.3.

## Soluzione

Di seguito sono riportate le opzioni per evitare il problema:

* Aggiorna l’applicazione Adobe Commerce alla versione 2.2.10 o 2.3.3. (per le istruzioni, consulta la [versione dell&#39;aggiornamento di Adobe Commerce sull&#39;infrastruttura cloud](https://devdocs.magento.com/guides/v2.3/cloud/project/project-upgrade.html) nella documentazione per gli sviluppatori).
* Se possibile, evita di limitare l’ambito del ruolo utente amministratore in base al sito web.
* [Inviare un ticket di supporto di Magento](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), per richiedere una patch, se disponibile.

## Lettura correlata

* [Ruoli utente](https://docs.magento.com/m2/ee/user_guide/system/permissions-user-roles.html) nella guida utente.
