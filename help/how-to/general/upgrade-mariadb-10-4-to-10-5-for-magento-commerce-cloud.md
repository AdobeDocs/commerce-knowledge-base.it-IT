---
title: Aggiornamento da MariaDB 10.4 a 10.5 per Adobe Commerce su cloud
description: MariaDB 10.4 raggiunge la fine del supporto il 18 giugno 2024. Questo articolo spiega come aggiornare MariaDB dalla versione 10.4 alla versione 10.5 per continuare a utilizzare Adobe Commerce sull’infrastruttura cloud.
feature: Best Practices, Cloud
exl-id: 065840b8-28c1-4686-95fc-df3e73152845
source-git-commit: 11f2fae3264a61413c5da1b93ef4980151a1df1e
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# Aggiornamento da MariaDB 10.4 a 10.5 per Adobe Commerce su cloud

MariaDB è un database open source aziendale utilizzato con Adobe Commerce.

MariaDB 10.4 raggiunge la fine del supporto il [18 giugno 2024](https://endoflife.date/mariadb). Non si è più conformi allo standard PCI quando si utilizza una versione non supportata di MariaDB. Questo articolo spiega come effettuare l’aggiornamento da MariaDB 10.4 a 10.5 per continuare a utilizzare Adobe Commerce sull’infrastruttura cloud.

>[!NOTE]
>
>Poiché MariaDB 10.4 raggiunge la fine del ciclo di vita (EOL), non sarà più supportato nelle versioni attuali di Adobe Commerce. È consigliabile disconnettersi da qualsiasi versione EOL entro 30 giorni dalla fine del ciclo di vita.

## Prodotto e versioni interessati

* Tutte le soluzioni Adobe Commerce on-premise e su infrastruttura cloud 2.4.4 e 2.4.5

## Soluzione

Adottare le nuove patch per sola sicurezza (2.4.4-p9 o 2.4.5-p8) rilasciate l’11 giugno 2024, per garantire la compatibilità con MariaDB 10.5. Quindi, segui i passaggi seguenti per effettuare l’aggiornamento da MariaDB 10.4 a 10.5.

### Passaggi per l’aggiornamento delle implementazioni cloud

1. Creare un [Database backup utilizzando i comandi di backup del database ECE-Tools](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots). Questo backup deve essere eseguito prima dei passaggi 2 e 3 in caso di errori durante l’aggiornamento di tabelle/righe.
1. [Verifica e converti tutte le tabelle compatte in tabelle dinamiche](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/maintenance/mariadb-upgrade). Questo passaggio è necessario per evitare potenziali perdite di dati durante l’aggiornamento del database.
1. Seleziona per tabelle MYISAM. È necessario [convertire tutte le tabelle MyISAM in InnoD](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud).
1. Dopo aver preparato le tabelle e le righe del database (i due passaggi precedenti), creare un [Database backup utilizzando i comandi di backup del database ECE-Tools](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots).
1. [Apri un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) per pianificare l&#39;aggiornamento da MariaDB 10.4 a 10.5. Nel ticket, specificare la data e l&#39;ora in cui si desidera aggiornare il DB. Il team di supporto ha bisogno di 48 ore di preavviso e il team di sviluppo del commerciante deve essere disponibile. Una volta concordate l&#39;ora e la data dell&#39;aggiornamento, effettuare le seguenti operazioni:
   1. Attiva la modalità di manutenzione per il sito e interrompi tutte le attività DB, ad esempio le attività Crons.
   1. Creare un [Database backup utilizzando i comandi di backup del database ECE-Tools](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots).
   1. Comunicare al supporto che il backup è stato completato tramite il ticket di supporto. Per visualizzare e tenere traccia dei biglietti, consulta [Guida utente di Adobe Commerce Help Center: tenere traccia dei ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) nella nostra knowledge base di supporto.
   1. Il team di supporto Adobe Commerce avvia quindi il processo di aggiornamento di MariaDB. Se sono stati eseguiti tutti i passaggi precedenti e il database ha dimensioni medie, il processo richiede circa un&#39;ora. I database più grandi richiedono più tempo. Una volta completato l’aggiornamento, potrai essere informato tramite il tuo ticket.
1. Disattiva la modalità di manutenzione. Fai riferimento a [Attiva o disattiva la modalità di manutenzione](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) nella documentazione per gli sviluppatori.

>[!NOTE]
>
>Si consiglia di creare un backup del database prima e dopo ogni passaggio di aggiornamento per eliminare ogni possibilità di perdita di dati. In questo modo sarà possibile eseguire il rollback a un passaggio precedente se si verificano problemi in qualsiasi momento durante l’aggiornamento della versione.

## Lettura correlata

* [Guida alle best practice per l’aggiornamento del database](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/prepare/prerequisites) per implementazioni locali.
* [Aggiornamento da MariaDB 10.0 a 10.2 per Adobe Commerce su cloud](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/upgrade-mariadb-10-0-to-10-2-for-magento-commerce-cloud) nella nostra knowledge base di supporto.
* [criteri del ciclo di vita Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/lifecycle-policy) nella documentazione per gli sviluppatori.
