---
title: Aggiornamento da MariaDB 10.0 a 10.2 per Adobe Commerce su cloud
description: MariaDB 10.0 e 10.1 sono alla fine del ciclo di vita (EOL). [Supporto terminato rispettivamente il 31 marzo 2019 e il 17 ottobre 2020](https://endoflife.date/mariadb). Questo articolo spiega come aggiornare MariaDB da 10.0 a 10.2 o da 10.2 a 10.3 o a 10.4, per utilizzare Adobe Commerce sull’infrastruttura cloud.
exl-id: bf66798b-f05c-482f-a2b4-b9bef92b0bab
feature: Best Practices, Cloud
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# Aggiornamento da MariaDB 10.0 a 10.2 per Adobe Commerce su cloud

MariaDB 10.0 e 10.1 sono alla fine del ciclo di vita (EOL). [Supporto terminato rispettivamente il 31 marzo 2019 e il 17 ottobre 2020](https://endoflife.date/mariadb). Questo articolo spiega come aggiornare MariaDB da 10.0 a 10.2 o da 10.2 a 10.3 o a 10.4, per utilizzare Adobe Commerce sull’infrastruttura cloud.

>[!NOTE]
>
>MariaDB 10.0 è la fine del ciclo di vita (EOL) e non è supportata nelle versioni correnti di Adobe Commerce. È consigliabile disconnettersi da qualsiasi versione EOL entro 30 giorni dalla fine del ciclo di vita.

## Prodotto e versioni interessati

* MariaDB 10.2 è consigliato per Adobe Commerce su infrastruttura cloud 2.3.x.
* MariaDB 10.4 è raccomandato per 2.4.x. MariaDB 10.3 è compatibile anche con Adobe Commerce su infrastruttura cloud 2.4.x.

## Passaggi di aggiornamento

La procedura seguente illustra come effettuare l&#39;aggiornamento da MariaDB 10.0 a 10.2 o da 10.2 a 10.3 o a 10.4:

1. Creare un backup di [DB utilizzando i comandi di backup del database ECE-Tools](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots). Questa operazione deve essere eseguita prima dei passaggi 2 e 3 in caso di problemi durante l’aggiornamento di tabelle/righe.
1. [Controllare e convertire tutte le tabelle compatte in tabelle dinamiche](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.html). Ciò è necessario per evitare potenziali perdite di dati durante l’aggiornamento del database.
1. Seleziona per tabelle MYISAM. [convertire tutte le tabelle MyISAM in InnoD](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html).
1. Dopo aver preparato le tabelle e le righe del database (i due passaggi precedenti), creare un backup di [DB utilizzando i comandi di backup del database ECE-Tools](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots).
1. [Aprire un ticket di supporto](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) per pianificare l&#39;aggiornamento da MariaDB 10.0 a 10.2 o da 10.2 a 10.3 o 10.4. Nel dettaglio del ticket, la data e l’ora in cui desideri aggiornare il DB. Il team di supporto ha bisogno di un preavviso di 48 ore e il team di sviluppo merchants deve essere disponibile. Una volta concordate l&#39;ora e la data dell&#39;aggiornamento, effettuare le seguenti operazioni:
   1. Metti il tuo sito in modalità di manutenzione e interrompi tutte le attività DB, ad esempio i client.
   1. Creare un backup di [DB utilizzando i comandi di backup del database ECE-Tools](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots).
   1. Comunicare al supporto che il backup è stato completato. Effettua questa operazione tramite il tuo ticket di supporto. Per visualizzare e tenere traccia dei biglietti, consulta la [Guida utente del Centro assistenza Adobe Commerce: tieni traccia dei biglietti](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#track-tickets) nella nostra knowledge base di supporto.
   1. Il team di supporto Adobe Commerce inizierà il processo di aggiornamento di MariaDB. Se sono stati eseguiti tutti i passaggi precedenti e il database ha dimensioni medie, è possibile eseguire l&#39;operazione in circa un&#39;ora. I database più grandi richiederanno più tempo. Riceverai informazioni tramite il ticket una volta completato l’aggiornamento.
1. Disattiva la modalità di manutenzione. Consulta [Abilitare o disabilitare la modalità di manutenzione](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sui requisiti di Adobe Commerce 2.4.x, consulta [Requisiti di sistema di Adobe Commerce 2.4 > Database](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements#database) nella documentazione per gli sviluppatori.
