---
title: Come includere un membro del team nelle notifiche di supporto
description: Questo articolo spiega come includere un membro del team nelle notifiche di supporto.
feature: Cloud, Support, Admin Workspace
role: Admin, Developer
exl-id: 63ea3f60-a509-447c-ac3d-bb2133141c80
source-git-commit: 6a4c1115aa92663ce12ce848dc583538e155509b
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---

# Come includere un membro del team nelle notifiche di supporto

Questo articolo spiega come includere un membro del team per ricevere automaticamente gli aggiornamenti del supporto tramite notifiche e-mail.

## Prodotti e versioni interessati

* Adobe Commerce sull&#39;infrastruttura cloud, tutte le [versioni supportate](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Causa

* Il membro del team non è stato aggiunto a [!DNL cloud project] con i privilegi necessari.
* Il membro del team non dispone di un account di supporto.

## Soluzione

1. Passare a **[!DNL Cloud Project URL]** (esempio: `https://us-3.magento.cloud/projects/xxxxxx/edit`).
1. Verificare se il membro del team è stato aggiunto al progetto ed è un [!DNL Super User].

Se non sono stati aggiunti al progetto, dovrai aggiungerli come [!DNL Super User] e concedere [!DNL Shared Access]:

* [Gestire l&#39;accesso utente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=it) nella guida utente.
* [Impossibile aggiungere l&#39;utente al progetto cloud Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-add-user-adobe-commerce-cloud-project.html?lang=it) nella Knowledge Base di Commerce.
* [Guida utente di Adobe Commerce Help Center: accesso condiviso](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=it#shared-access) nella Knowledge Base di Commerce.

Se sono stati aggiunti a [!DNL cloud project], ma non dispongono di [!DNL Super User role], aggiorna di conseguenza [!DNL role] in [Gestisci accesso utente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=it).

Se desideri consentire a un membro del team di essere un osservatore in tutti i casi aperti per la tua organizzazione, invia un [ticket di supporto](https://experienceleague.adobe.com/home?lang=it&support-tab=home#support).

## Lettura correlata

[Gli ex membri del team ricevono le e-mail di notifica cloud di Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/former-teammembers-receive-cloud-notification-emails.html?lang=it)
