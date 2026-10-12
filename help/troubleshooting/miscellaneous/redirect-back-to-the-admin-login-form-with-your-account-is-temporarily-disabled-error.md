---
title: Reindirizza al modulo di accesso di [!UICONTROL Commerce Admin] con l'errore "L'account è temporaneamente disabilitato"
description: 'Questo articolo fornisce le possibili soluzioni per il problema di accesso dell’amministratore di Commerce, in cui si viene reindirizzati al modulo di accesso con il seguente messaggio di errore: *"L’account è temporaneamente disabilitato"*. La soluzione suggerita consiste nel controllare e correggere le impostazioni del database utente amministratore.'
exl-id: 1c7ffa1c-1fb1-4f69-9534-77d1e119318a
feature: Admin Workspace, Customer Service
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
  - id: deedbb4d-f1b7-58ea-a34a-de1f481f9d4c
    internal-label: Customer Service
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '256'
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
1. Utilizzare uno strumento di database come [[!DNL phpMyAdmin]](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/optional-software#phpmyadmin) oppure accedere manualmente al database dalla riga di comando. Nella tabella del database `admin_user`, per il record utente amministratore, verificare se `is_active` è impostato su &quot;`1`&quot; e `lock_expires` è `NULL`. Se necessario, reimpostare questi valori.

## Lettura correlata

* [Best practice per la modifica delle tabelle del database](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) nel playbook di implementazione di Commerce
