---
title: Errore "Versione corrente di RDBMS non supportata" durante la distribuzione
description: "Questo articolo fornisce una soluzione per i casi in cui una distribuzione non riesce e si verifica il seguente errore nel registro di distribuzione: *la versione corrente di RDBMS non è supportata*."
exl-id: e7300f64-5749-4de8-b4d2-bc4789437282
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---

# Errore &quot;Versione corrente di RDBMS non supportata&quot; durante la distribuzione

Questo articolo fornisce una soluzione per i casi in cui una distribuzione non riesce e si verifica il seguente errore nel registro di distribuzione: *la versione corrente di RDBMS non è supportata*.

## Prodotti e versioni interessati

Adobe Commerce sull’infrastruttura cloud, 2.3.0-2.3.7-p1, 2.4.0-2.4.3.

## Problema

Questo messaggio di errore indica che la versione corrente di MariaDB non è più supportata nella versione di Adobe Commerce a cui si sta tentando di eseguire l’aggiornamento e che MariaDB deve essere aggiornato a una versione compatibile.


<u>Passaggi da riprodurre</u>:

Tentativo di distribuzione.

<u>Risultato previsto</u>:

Distribuzione riuscita.

<u>Risultato effettivo</u>:

Distribuzione non riuscita con messaggio di errore: *la versione corrente di RDBMS non è supportata*.

## Causa

La versione di MariaDB in uso non è compatibile con la versione di Adobe Commerce a cui si sta tentando di eseguire l&#39;aggiornamento.

## Soluzione

Prima di aggiornare l&#39;applicazione, è necessario aggiornare il servizio MariaDB a una versione compatibile.


Per il ramo di integrazione su Adobe Commerce su infrastruttura cloud Architettura del piano Pro (e tutti i rami nell&#39;architettura Starter), segui [Configurazione del servizio](https://devdocs.magento.com/cloud/project/services.html) nella documentazione per gli sviluppatori.

Per l&#39;architettura di staging e produzione su Adobe Commerce su infrastruttura cloud Pro, [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) per richiedere l&#39;aggiornamento dei servizi prima di distribuire l&#39;aggiornamento della versione di Adobe Commerce.


## Lettura correlata

* [Best practice per le build e la distribuzione](https://devdocs.magento.com/cloud/reference/discover-deploy.html#best-practices) nella documentazione per gli sviluppatori.
* [Aggiornamento Adobe Commerce 2.3.5: compatta in tabelle dinamiche](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.html) nella knowledge base di supporto.
