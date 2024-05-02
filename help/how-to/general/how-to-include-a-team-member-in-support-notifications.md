---
title: Come includere un membro del team nelle notifiche di supporto
description: Questo articolo spiega come includere un membro del team nelle notifiche di supporto.
feature: Cloud, Support, Admin Workspace
role: Admin, Developer
exl-id: 63ea3f60-a509-447c-ac3d-bb2133141c80
source-git-commit: 1c568d75534bbfe322d9f980b40c5dd64fc5b7a2
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# Come includere un membro del team nelle notifiche di supporto

Questo articolo spiega come includere un membro del team per ricevere automaticamente gli aggiornamenti del supporto tramite notifiche e-mail.

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud, tutto [versioni supportate](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Causa

* Il membro del team non è stato aggiunto al [!DNL cloud project] con i privilegi necessari.
* Il membro del team non dispone di un account di supporto.

## Soluzione

1. Vai a **[!DNL Cloud Project URL]** (Esempio: `https://us-3.magento.cloud/projects/xxxxxx/edit`).
1. Verifica se il membro del team è stato aggiunto al progetto e [!DNL Super User].

Se non richiedono [!DNL cloud project] , invia una [Richiesta di supporto presso il Centro di supporto Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) a automaticamente CC: loro su tutti i biglietti, e anche fornire loro **[!DNL MAGE ID]** (se disponibile).

Se non sono state aggiunte al progetto, dovrai aggiungerle come [!DNL Super User] e concessione [!DNL Shared Access]:

* [Gestire l’accesso degli utenti](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) nella guida utente.
* [Impossibile aggiungere l’utente al progetto cloud Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-add-user-adobe-commerce-cloud-project.html) nella Knowledge Base di Commerce.
* [Guida utente di Adobe Commerce Help Center: accesso condiviso](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#shared-access) nella Knowledge Base di Commerce.

Se sono stati aggiunti al [!DNL cloud project], ma non hanno il [!DNL Super User role], aggiorna i [!DNL role] di conseguenza in [Gestire l’accesso degli utenti](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html).

## Lettura correlata

[Gli ex membri del gruppo ricevono le e-mail di notifica cloud di Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/former-teammembers-receive-cloud-notification-emails.html)
