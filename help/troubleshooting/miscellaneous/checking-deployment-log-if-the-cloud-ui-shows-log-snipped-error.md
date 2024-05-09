---
title: Verifica del registro di distribuzione se nell’interfaccia utente di Cloud è presente l’errore "log snipped"
description: Questo articolo fornisce una soluzione per il problema relativo all’interfaccia utente di Adobe Commerce sull’infrastruttura cloud, dove viene visualizzato il messaggio di errore *log snipped a causa della lunghezza eccessiva* durante il tentativo di visualizzare il registro di distribuzione nell’interfaccia utente del progetto cloud.
exl-id: 04d28741-72c1-4722-be46-425fe136b9a6
feature: Cloud, Deploy, Logs, Paas
role: Developer
source-git-commit: 71bec5b99063d771982f6dcab111b9e5a4aaec69
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# Verifica del registro di distribuzione se l’interfaccia utente cloud dispone di *log snipped* errore

Questo articolo fornisce una soluzione per il problema in cui l’interfaccia utente di Adobe Commerce sull’infrastruttura cloud mostra *registro troncato perché troppo lungo* messaggio di errore durante il tentativo di visualizzare il registro di distribuzione nell’interfaccia utente del progetto cloud. (Non si applica al [Console Adobe Commerce Cloud](https://console.adobecommerce.com/).)

## Prodotti interessati

Adobe Commerce su infrastruttura cloud (tutte le versioni supportate)

## Problema

Quando tenti di visualizzare il registro di distribuzione nell’interfaccia utente del progetto cloud, l’interfaccia utente di Adobe Commerce nell’infrastruttura cloud mostra il seguente messaggio di errore: *registro troncato perché troppo lungo*.

## Passaggi da riprodurre

1. Vai all’URL del progetto e fai clic su **Stato** dell’impiego in questione.
1. Se il registro è troppo lungo per essere visualizzato nell’interfaccia utente, verrà visualizzato il messaggio di errore: *registro troncato perché troppo lungo*.

## Causa

Tieni presente che il registro visualizzato nell’interfaccia utente non deve essere trattato come l’origine della verità, soprattutto se scopri che il sito non risponde o non funziona correttamente dopo che la distribuzione è stata elencata con lo stato di Operazione completata. È inoltre necessario verificare con i registri sul server. Fai riferimento a [Visualizzare e gestire i registri](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html) nella documentazione per gli sviluppatori.

## Soluzione

1. Assicurati di avere [CLI Magento Cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html) installato nell’ambiente locale.
1. Esegui il comando seguente:

   ```bash
   magento-cloud activity -p <project id> -e <environment>
   ```

1. Restituisce un output simile al seguente:

   ```bash
   Activities on the project <project name> (project id), environment <environment>:
   +---------------+---------------------------+-------------------------------------+----------+----------+---------+
   | ID            | Created                   | Description                         | Progress | State    | Result  |
   +---------------+---------------------------+-------------------------------------+----------+----------+---------+
   | l5wgwmzwrsskg | 2021-06-01T08:18:02-07:00 | ABC merged Integration into Staging | 100%     | complete | success |
   | raah5xrhqz3wg | 2021-06-01T08:07:18-07:00 | XYZ pushed to Integration           | 100%     | complete | failure |
   ```

1. Copia l’ID attività della distribuzione interessata, quindi esegui il comando:

   ```bash
   magento-cloud activity:log <activity ID> -p <project id> -e <environment>
   ```

   Esempio per esaminare il registro della distribuzione non riuscita:

   ```bash
   magento-cloud activity:log raah5xrhqz3wg -p <project id> -e <environment>
   ```

## Letture correlate nella documentazione per gli sviluppatori:

* [Adobe Commerce su infrastruttura cloud > Genera e implementa](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html)
* [Adobe Commerce su infrastruttura cloud > Visualizza e gestisci i registri](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html)
