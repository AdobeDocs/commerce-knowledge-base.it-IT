---
title: Impossibile aggiungere l’utente al progetto cloud Adobe Commerce
description: Questo articolo fornisce una soluzione per i casi in cui non è possibile aggiungere un utente a un progetto cloud di Adobe Commerce.
exl-id: 59940916-bf92-4e89-a6f9-bca87c54125c
feature: Cloud, Paas
role: Developer
source-git-commit: af74d944553c34da2ac8343695bca49f971bc4e5
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# Impossibile aggiungere l’utente al progetto cloud Adobe Commerce

Questo articolo fornisce una soluzione per quando si tenta di aggiungere un utente a un progetto cloud, ma non riesce e viene visualizzato un errore: *L&#39;utente XXX non esiste*.

## Prodotti e versioni interessati

* Adobe Commerce sull&#39;infrastruttura cloud, [tutte le versioni supportate](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problema

Questo articolo fornisce una soluzione per i casi in cui non è possibile aggiungere un utente a un progetto cloud di Adobe Commerce.

## Causa

Questo è il comportamento previsto. Per poter essere aggiunto come utente al progetto, l’account dell’utente deve prima essere creato all’indirizzo https://accounts.magento.cloud e collegato al relativo SSO di Adobe.

## Soluzione

1. Chiedere all&#39;utente di accedere al proprio account all&#39;indirizzo https://accounts.magento.cloud (deve essersi già registrato per un account all&#39;indirizzo adobe.com con tale indirizzo e-mail. La creazione o l&#39;utilizzo di un account in https://account.adobe.com non implica automaticamente che l&#39;utente disponga di un account in https://accounts.magento.cloud)
Nota: se l’utente ha avuto un account su account.magento.com o accounts.magento.cloud prima di agosto 2022, potrebbe non avere un account con/su adobe.com a meno che non l’abbia creato ad agosto 2022 o successivamente. Se l&#39;utente non dispone di un account Adobe e non è in grado di accedere, [invia una richiesta di supporto](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) all&#39;indirizzo https://experienceleague.adobe.com/home#support e fornisci i dettagli (Motivo del problema = Gestione utente).
1. L’utente deve quindi passare a https://accounts.magento.cloud.
1. Dopo averlo fatto, dovresti essere in grado di aggiungere l’utente al progetto. Per i passaggi, consulta [Aggiungere utenti e gestire l&#39;accesso](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#add-users-and-manage-access) nella guida Commerce on Cloud Infrastructure.

## Lettura correlata:

* [Gestire l&#39;accesso degli utenti](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) nella Guida all&#39;infrastruttura di Commerce su Cloud.
* [Impossibile accedere al supporto Adobe Commerce o all&#39;account cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-to-log-in-to-support-or-cloud-project.html)
