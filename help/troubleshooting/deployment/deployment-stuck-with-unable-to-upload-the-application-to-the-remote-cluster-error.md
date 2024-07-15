---
title: Distribuzione bloccata con errore "Impossibile caricare l’applicazione nel cluster remoto"
description: '"Questo articolo fornisce una soluzione al problema di Adobe Commerce, in cui la distribuzione si blocca, e il seguente messaggio di errore è disponibile nel registro di distribuzione: *"Errore: impossibile caricare l’applicazione nel cluster remoto"*."'
exl-id: 30f0ec31-db27-429c-b065-cf7770a72194
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# Distribuzione bloccata con errore &quot;Impossibile caricare l’applicazione nel cluster remoto&quot;

Questo articolo fornisce una soluzione per il problema di Adobe Commerce, in cui la distribuzione si blocca e nel registro di distribuzione è possibile trovare il seguente messaggio di errore: *&quot;Errore: impossibile caricare l&#39;applicazione nel cluster remoto&quot;*.

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud, tutte le versioni

## Problema

<u>Passaggi da riprodurre</u>:

Attiva la distribuzione manualmente o eseguendo un’unione, un push o una sincronizzazione dell’ambiente.

<u>Risultato previsto</u>:

Distribuzione completata correttamente.

<u>Risultato effettivo</u>:

La distribuzione si blocca e nel registro degli errori di distribuzione nell&#39;interfaccia utente del cloud viene visualizzato il seguente messaggio di errore: *&quot;Errore: impossibile caricare l&#39;applicazione nel cluster remoto&quot; trovato nel registro di distribuzione dopo la distribuzione non riuscita. Il sito potrebbe visualizzare l&#39;errore &quot;Timeout del primo byte 503&quot;*.

## Causa

Il problema è causato dall&#39;interruzione dello storage disponibile.

## Soluzione

È possibile pulire le directory di registro e/o aumentare lo spazio su disco.

Directory da considerare per la pulizia:

* `var/log`
* `var/report`
* `var/debug/`
* `var`

Per informazioni dettagliate su come aumentare lo spazio su disco se si utilizza l&#39;architettura del piano Starter per l&#39;infrastruttura cloud di Adobe Commerce, vedere [Aumentare lo spazio su disco per l&#39;ambiente di integrazione sul cloud](/help/how-to/general/increase-disk-space-for-integration-environment-on-cloud.md) nella knowledge base del supporto. Le stesse istruzioni possono essere utilizzate per aumentare lo spazio dell’ambiente di integrazione dell’architettura Pro plan Adobe Commerce sull’infrastruttura cloud. Per Pro Production/Staging, è necessario [inviare un ticket al supporto Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket-Submit-a-support-ticket) e richiedere maggiore spazio su disco. In genere, tuttavia, non è necessario occuparsi di questo problema nella fase di staging/produzione del piano Pro, in quanto Adobe Commerce monitora questi parametri per te e avvisa e/o intraprende azioni in base al contratto.
