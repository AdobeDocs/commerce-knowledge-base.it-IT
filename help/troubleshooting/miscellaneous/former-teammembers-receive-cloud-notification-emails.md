---
title: Gli ex membri del gruppo ricevono le e-mail di notifica cloud di Adobe Commerce
description: Questo articolo fornisce una soluzione per l’invio di e-mail di notifica sull’infrastruttura cloud di Adobe Commerce ai membri del team precedente.
exl-id: b2535f66-8aec-4ddf-9a69-60879a0a1939
feature: Cloud, Communications, Paas
role: Developer
source-git-commit: bd199fac6d8f33491b9fa0f508b2bb52d56b46a5
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 0%

---

# Gli ex membri del gruppo ricevono le e-mail di notifica cloud di Adobe Commerce

Questo articolo fornisce una soluzione per rimuovere dall’elenco dei destinatari le e-mail di notifica che sono:

* Ex membri del team non più associati al progetto.
* Membri attuali del team che non dovrebbero ricevere le notifiche.

## Problema

È stato inviato al team un avviso di interruzione rilevata o di un problema importante relativo al progetto/ambiente cloud. Ciò include i membri che potrebbero non essere più associati al progetto, ad esempio sviluppatori esterni/di agenzie o integratori di sistemi. Desideri che questi utenti non ricevano più le notifiche.

## Soluzione

>[!NOTE]
>
>Se sei uno sviluppatore esterno/di agenzia o un integratore di sistemi e non sei più associato al progetto, devi contattare il Proprietario del progetto o l’Amministratore del progetto per assistenza.

Esistono due modi per interrompere le notifiche rimuovendo gli utenti dal progetto:

* Metodo 1: utilizzo del cloud [!DNL Project URL]. Per ulteriori informazioni, consulta [Gestire l&#39;accesso degli utenti](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=it) nella guida all&#39;infrastruttura cloud di Commerce.
* Metodo 2: utilizzo del cloud magento [!DNL CLI]. Per ulteriori informazioni, consulta [Gestire gli utenti con  [!DNL CLI]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=it#manage-users-with-the-cli) nella guida all&#39;infrastruttura cloud di Commerce.

Se questa operazione è già stata eseguita e le notifiche e-mail continuano a includere tali utenti, inviare un ticket di supporto per richiedere la rimozione dall&#39;impostazione *[!UICONTROL Always CC]* dell&#39;account.

## Lettura correlata

* [Visualizza il ruolo di progetto di un utente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=it#view-a-user&?lang=it#39;s-project-role) nella guida Commerce su infrastruttura cloud.
* [Come includere un membro del team nelle notifiche di supporto](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-include-a-team-member-in-support-notifications.html?lang=it) nella KB di Commerce.
