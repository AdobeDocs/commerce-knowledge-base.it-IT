---
title: Gli ex membri del gruppo ricevono le e-mail di notifica cloud di Adobe Commerce
description: Questo articolo fornisce una soluzione per l’invio di e-mail di notifica sull’infrastruttura cloud di Adobe Commerce ai membri del team precedente.
exl-id: b2535f66-8aec-4ddf-9a69-60879a0a1939
feature: Cloud, Communications, Paas
role: Developer
source-git-commit: 075f295c5b600fcca9fbecc5aad20b0640d900f9
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Gli ex membri del gruppo ricevono le e-mail di notifica cloud di Adobe Commerce

Questo articolo fornisce una soluzione per la ricezione di notifiche da parte dei membri del team non più associati al progetto.

## Problema

È stato inviato al team un avviso di interruzione rilevata o di un problema importante relativo al progetto/ambiente cloud. Ciò include i membri che potrebbero non essere più associati al progetto, ad esempio sviluppatori esterni/di agenzie o integratori di sistemi. Desideri che questi utenti non ricevano più le notifiche.

## Soluzione

Esistono due modi per interrompere le notifiche rimuovendo gli utenti dal progetto:

* Metodo 1: Utilizzo del cloud [!DNL Project URL]. Fai riferimento a [Gestire l’accesso degli utenti](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) nella guida Commerce su infrastruttura cloud per i passaggi.
* Metodo 2: Utilizzo di magento-cloud [!DNL CLI]. Fai riferimento a [Gestire gli utenti con [!DNL CLI]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#manage-users-with-the-cli) nella guida Commerce su infrastruttura cloud per i passaggi.

Se ciò è già stato fatto e le notifiche e-mail continuano a includere tali utenti, invia un ticket di supporto per richiedere che vengano rimossi dal *[!UICONTROL Always CC]* impostazione dell&#39;account.

## Lettura correlata

* [Visualizzare il ruolo di progetto di un utente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#view-a-user’s-project-role) nella guida all’infrastruttura cloud di Commerce.
* [Come includere un membro del team nelle notifiche di supporto](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-include-a-team-member-in-support-notifications.html) nella KB di Commerce.
