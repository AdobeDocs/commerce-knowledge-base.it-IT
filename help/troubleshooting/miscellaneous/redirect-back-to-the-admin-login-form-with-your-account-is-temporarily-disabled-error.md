---
title: '''Reindirizza al modulo di accesso di [!UICONTROL Commerce Admin] con l''errore "L''account è temporaneamente disabilitato"'
description: '"Questo articolo illustra le possibili soluzioni per il problema di accesso dell’amministratore di Commerce, in cui si viene reindirizzati al modulo di accesso con il seguente messaggio di errore: *"L’account è temporaneamente disabilitato"*. La soluzione suggerita consiste nel controllare e correggere le impostazioni del database utente amministratore.'''
exl-id: 1c7ffa1c-1fb1-4f69-9534-77d1e119318a
feature: Admin Workspace, Customer Service
role: Developer
source-git-commit: f87263cde5aa001f78abc368c949ce150feecb91
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 0%

---

# Reindirizza al modulo di accesso di [!UICONTROL Commerce Admin] con l&#39;errore &quot;L&#39;account è temporaneamente disabilitato&quot;

Questo articolo fornisce le possibili soluzioni per il problema di accesso [!UICONTROL Commerce Admin], in cui si viene reindirizzati al modulo di accesso con il seguente messaggio di errore: *&quot;L&#39;account è temporaneamente disabilitato&quot;*. La soluzione suggerita consiste nel controllare e correggere le impostazioni del database utente amministratore.

## Edizioni e versioni interessate:

Tutte le versioni e le edizioni di Adobe Commerce

## Problema

<u>Passaggi da riprodurre</u>:

1. Passare alla pagina **[!UICONTROL Commerce Admin]**.
1. Immetti le tue credenziali e fai clic su **Accedi**.

<u>Risultato previsto</u>:

Si è connessi a [!UICONTROL Commerce Admin].

<u>Risultato effettivo</u>:

Sei stato reindirizzato al modulo di accesso, con il seguente messaggio di errore visualizzato: *&quot;Il tuo account è temporaneamente disabilitato. Riprovare più tardi&quot;*.

## Soluzione

1. Creare un backup del database.
1. Utilizzare uno strumento di database come [[!DNL phpMyAdmin]](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/optional.html#install-optional-phpmyadmin) oppure accedere manualmente al database dalla riga di comando. Nella tabella del database `admin_user`, per il record utente amministratore, verificare se `is_active` è impostato su &quot;`1`&quot; e `lock_expires` è `NULL`. Se necessario, reimpostare questi valori.

## Lettura correlata

* [Reindirizza al modulo di accesso senza errori quando si tenta di accedere a [!UICONTROL Commerce Admin]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/login-redirect-when-trying-to-login-to-magento-admin)
* [Best practice per la modifica delle tabelle del database](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) nel playbook di implementazione di Commerce
