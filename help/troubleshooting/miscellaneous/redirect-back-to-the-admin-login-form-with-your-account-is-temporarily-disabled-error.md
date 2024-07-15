---
title: Reindirizza al modulo di accesso dell’amministratore di Commerce con l’errore "L’account è temporaneamente disabilitato"
description: '"Questo articolo illustra le possibili soluzioni per il problema di accesso dell’amministratore di Commerce, in cui si viene reindirizzati al modulo di accesso con il seguente messaggio di errore: *"L’account è temporaneamente disabilitato"*. La soluzione suggerita consiste nel controllare e correggere le impostazioni del database utente amministratore.'''
exl-id: 1c7ffa1c-1fb1-4f69-9534-77d1e119318a
feature: Admin Workspace, Customer Service
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---

# Reindirizza al modulo di accesso dell’amministratore di Commerce con l’errore &quot;L’account è temporaneamente disabilitato&quot;

Questo articolo fornisce le possibili soluzioni per il problema di accesso dell&#39;amministratore di Commerce, in cui si viene reindirizzati al modulo di accesso con il seguente messaggio di errore: *&quot;L&#39;account è temporaneamente disabilitato&quot;*. La soluzione suggerita consiste nel controllare e correggere le impostazioni del database utente amministratore.

## Edizioni e versioni interessate:

Tutte le versioni e le edizioni di Adobe Commerce

## Problema

<u>Passaggi da riprodurre</u>:

1. Vai alla pagina di amministrazione di Commerce.
1. Immetti le credenziali e fai clic su Accedi.

<u>Risultato previsto</u>:

Hai effettuato l’accesso a Commerce Admin.

<u>Risultato effettivo</u>:

Sei stato reindirizzato al modulo di accesso, con il seguente messaggio di errore visualizzato: *&quot;Il tuo account è temporaneamente disabilitato. Riprovare più tardi&quot;*.

## Soluzione

1. Creare un backup del database.
1. Utilizzare uno strumento di database come [phpMyAdmin](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/optional.html#install-optional-phpmyadmin) oppure accedere al database manualmente dalla riga di comando. Nella tabella del database `admin_user`, per il record utente amministratore, verificare se `is_active` è impostato su &quot;`1`&quot; e `lock_expires` è `NULL`. Se necessario, reimpostare questi valori.

## Lettura correlata nella knowledge base del supporto

* [Reindirizza al modulo di accesso senza errori quando tenti di accedere all’amministratore di Commerce](/help/troubleshooting/miscellaneous/login-redirect-when-trying-to-login-to-magento-admin.md)
