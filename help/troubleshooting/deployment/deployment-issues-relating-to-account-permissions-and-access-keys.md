---
title: Problemi di distribuzione relativi alle autorizzazioni dell’account e alle chiavi di accesso
description: Questo articolo fornisce una soluzione per i problemi relativi all’implementazione di Adobe Commerce su infrastrutture cloud causati da un conflitto di proprietà della chiave di accesso.
exl-id: e8d72ebe-453f-4d18-a25e-c76e685aa667
feature: Deploy, Roles/Permissions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# Problemi di distribuzione relativi alle autorizzazioni dell’account e alle chiavi di accesso

Questo articolo fornisce una soluzione per i problemi relativi all’implementazione di Adobe Commerce su infrastrutture cloud causati da un conflitto di proprietà della chiave di accesso.

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud, tutte le versioni supportate

## Problema

<u>Prerequisiti</u>:

La licenza Cloud è associata al contatto A (indirizzo e-mail: *<u>first@e.mail</u>*)

<u>Passaggi da riprodurre</u>:

1. Contatta Le chiavi di accesso di Adobe Commerce create sul loro account (chiave X) e installatele sul cloud.
1. Il contatto B (indirizzo di posta elettronica: *<u>second@e.mail</u>*) ha acquistato un&#39;estensione utilizzando il proprio account e ha creato le chiavi di accesso per l&#39;installazione dell&#39;estensione (chiave Y).
1. Il contatto A ha quindi lasciato la società e la licenza (proprietà) è stata trasferita al contatto B.
1. System Integrator tenta di installare l’estensione nell’ambiente cloud utilizzando la chiave X.

<u>Risultato previsto</u>:

Installazione dell&#39;estensione completata.

<u>Risultato effettivo</u>:

L&#39;estensione non è installata perché la distribuzione non riesce.

## Causa

Entrambe le chiavi vengono assegnate al ruolo di contatto, causando un conflitto.

## Soluzione

Se una distribuzione non è riuscita dopo che è stata apportata una modifica al contatto principale dell&#39;account (con l&#39;account originale e quello nuovo con le proprie chiavi di accesso) e le chiavi sono state trasferite dall&#39;account originale al nuovo account, è necessario disabilitare le chiavi dall&#39;account originale. Per quanto riguarda l’esempio precedente, la chiave X deve essere disabilitata.

### Come disattivare il tasto di scelta

Se non hai accesso all&#39;account [Commerce Marketplace](https://marketplace.magento.com/) associato alla chiave precedente, [contatta il supporto Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) per disabilitare la chiave.

Se hai accesso all’account Marketplace associato alla vecchia chiave, procedi come segue per disabilitare la chiave:

1. Accedi alla [Commerce Marketplace](https://marketplace.magento.com/) utilizzando le credenziali dell&#39;account precedente.
1. Fai clic sul nome dell&#39;account in alto a destra della pagina e seleziona **Il mio profilo**.
1. Fare clic su **Chiavi di accesso** nella scheda Marketplace.

   ![magento_products_access_keys_2.4.1.png](/help/troubleshooting/miscellaneous/assets/magento_products_access_keys_2.4.1.png)

1. Fai clic su **Disattiva** accanto alla chiave di accesso.

## Lettura correlata

* [Ottieni le chiavi di autenticazione](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/authentication-keys) nella documentazione per gli sviluppatori.
