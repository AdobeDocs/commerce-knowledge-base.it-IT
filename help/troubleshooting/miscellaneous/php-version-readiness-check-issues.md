---
title: Problemi relativi al controllo della disponibilità della versione PHP
description: In questo articolo vengono illustrate le soluzioni per i problemi di versione PHP che potrebbero verificarsi durante l'installazione o l'aggiornamento di Adobe Commerce on-premise tramite l'Installazione guidata Web.
exl-id: dee939cf-b9b2-4750-965c-5b8908a4498d
feature: Variables
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# Problemi relativi al controllo della disponibilità della versione PHP

In questo articolo vengono illustrate le soluzioni per i problemi di versione PHP che potrebbero verificarsi durante l&#39;installazione o l&#39;aggiornamento di Adobe Commerce on-premise tramite l&#39;Installazione guidata Web.

>[!WARNING]
>
>Sull’infrastruttura cloud di Adobe Commerce, tieni presente che gli aggiornamenti dei servizi non possono essere inviati all’ambiente di produzione senza un preavviso di 48 ore lavorative al nostro team di infrastruttura. Ciò è necessario in quanto è necessario disporre di un tecnico del supporto dell&#39;infrastruttura per aggiornare la configurazione entro l&#39;intervallo di tempo desiderato, riducendo al minimo i tempi di inattività dell&#39;ambiente di produzione. Quindi, 48 ore prima del momento in cui le modifiche devono essere in produzione [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) specificando l&#39;aggiornamento del servizio richiesto e indicando l&#39;ora in cui desideri avviare il processo di aggiornamento.

## Prodotti e versioni interessati

* Adobe Commerce on-premise 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x

## Versione PHP non supportata

### Problema

Il controllo non riesce perché si utilizza una versione PHP non supportata.

### Soluzione

Per risolvere questo problema, utilizza una delle versioni supportate elencate nella documentazione per gli sviluppatori [2.3.x Requisiti di sistema](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements) e [2.2.x Requisiti di sistema](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements).

## Il controllo di idoneità PHP non viene visualizzato

### Problema

Il controllo di preparazione PHP non visualizza la versione PHP, come illustrato nella figura riportata di seguito.
![upgr-tshoot-no-cron.png](assets/upgr-tshoot-no-cron.png)

### Soluzione

Sintomo di una configurazione errata del processo cron. Per ulteriori informazioni, consulta [Configurare i processi cron](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/next-steps/configuration) nella documentazione per gli sviluppatori.

## Versione PHP errata

### Problema

Il controllo segnala una versione PHP errata. In genere, questo accade solo agli utenti avanzati che hanno più versioni PHP installate. In alcuni casi, il controllo di idoneità ha esito negativo; in altri casi, potrebbe essere superato.

Se la versione PHP riportata dal controllo di fattibilità non è corretta, è il risultato di una mancata corrispondenza delle versioni PHP tra PHP CLI e il plug-in del server web. Adobe Commerce richiede di utilizzare *una versione* di PHP sia per CLI (che esegue cron) che per il server Web (che esegue Commerce Admin, Component Manager e System Upgrade).

### Soluzione

Supponiamo che se si ha questo problema, si è un utente avanzato che ha probabilmente installato più versioni di PHP sul sistema.

Per risolvere il problema, provare a eseguire le operazioni seguenti:

* Riavvia il server web o php-fm.
* Controllare la variabile di ambiente `$PATH` per individuare più percorsi a PHP.
* Utilizzare il comando `which php` per individuare il primo eseguibile PHP nel percorso. Se non è corretto, rimuoverlo o creare un collegamento simbolico alla versione PHP corretta.
* Utilizzare una pagina [`phpinfo.php`](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/optional-software) per raccogliere ulteriori informazioni.
* Assicurati di eseguire una versione PHP supportata in base ai nostri requisiti di sistema, nella documentazione per gli sviluppatori:
   * [Requisiti di sistema di Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements)
* Impostare le stesse impostazioni PHP sia per la riga di comando PHP che per il plug-in del server Web PHP, come descritto in [Opzioni di configurazione PHP](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements#php-settings) nella documentazione per gli sviluppatori.
