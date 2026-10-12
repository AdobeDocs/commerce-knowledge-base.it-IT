---
title: Gli ex membri del gruppo ricevono le e-mail di notifica cloud di Adobe Commerce
description: Questo articolo fornisce una soluzione per l’invio di e-mail di notifica sull’infrastruttura cloud di Adobe Commerce ai membri del team precedente.
exl-id: b2535f66-8aec-4ddf-9a69-60879a0a1939
feature: Cloud, Communications, Paas
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: bb03f6c4-cab9-560e-9d02-5816e1808d17
    internal-label: Communications
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '336'
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

* Metodo 1: utilizzo del cloud [!DNL Project URL]. Per ulteriori informazioni, consulta [Gestire l&#39;accesso degli utenti](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) nella guida all&#39;infrastruttura cloud di Commerce.
* Metodo 2: utilizzo del cloud magento [!DNL CLI]. Per ulteriori informazioni, consulta [Gestire gli utenti con  [!DNL CLI]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#manage-users-with-the-cli) nella guida all&#39;infrastruttura cloud di Commerce.

Se questa operazione è già stata eseguita e le notifiche e-mail continuano a includere tali utenti, inviare un ticket di supporto per richiedere la rimozione dall&#39;impostazione *[!UICONTROL Always CC]* dell&#39;account.

## Lettura correlata

* [Visualizza il ruolo di progetto di un utente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#view-a-user's-project-role) nella guida Commerce su infrastruttura cloud.
* [Come includere un membro del team nelle notifiche di supporto](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-include-a-team-member-in-support-notifications.html) nella KB di Commerce.
