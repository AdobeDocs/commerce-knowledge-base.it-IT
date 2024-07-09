---
title: Dipendenze dei componenti in conflitto
description: Questo articolo fornisce una soluzione per le dipendenze dei componenti in conflitto. Quando si tenta di configurare o aggiornare Adobe Commerce utilizzando l’Installazione guidata Web, viene visualizzato il messaggio di errore *"Sono state trovate dipendenze dei componenti in conflitto"* Compositore.
exl-id: 782049c4-b6e1-4ead-a00f-80d2aa8475c9
feature: Configuration
role: Developer
source-git-commit: 8f0f7412e75e07a22e66236b88c095c698dbf23e
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---

# Dipendenze dei componenti in conflitto

Questo articolo fornisce una soluzione per le dipendenze dei componenti in conflitto. Quando si tenta di configurare o aggiornare Adobe Commerce tramite l&#39;Installazione guidata Web, viene visualizzato il messaggio *&quot;Sono state rilevate dipendenze dei componenti in conflitto&quot;* Messaggio di errore del Compositore.

## Prodotti e versioni interessati

* Adobe Commerce on-premise 2.2.x, 2.3.x
* Adobe Commerce sull’infrastruttura cloud 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x


## Problema {#issue}

Un messaggio di errore relativo alle dipendenze dei componenti in conflitto è simile al seguente (i nomi e le versioni effettive dei pacchetti variano):

```bash
We found conflicting component dependencies.
You are trying to update package(s) magento/module-sample-data to 1.0.0-beta
We have detected conflicts with the following packages:
- magento/sample-data version 0.74.0-beta15. Please try to update it to one of the following package versions: 0.74.0-beta16, 0.74.0-beta14, 0.74.0-beta13, 0.74.0-beta12, 0.74.0-beta11, 0.74.0-beta10, 0.74.0-beta9, 0.74.0-beta8, 0.74.0-beta7
```

## Causa

Questo messaggio viene visualizzato se Composer non è in grado di determinare quali componenti installare o aggiornare.

## Soluzione

Due scenari principali possono causare conflitti tra le dipendenze dei componenti. Fai clic sullo scenario per ottenere i passaggi per la risoluzione dei problemi.

* [Aggiornamento di Adobe Commerce](#upgrading-magento)
* [Incompatibilità con moduli di terze parti:](#incompatibility-third-party-modules)
   * [Adobe Commerce (tutti i tipi di distribuzione)](#magento-commerce-magento-commerce-cloud)
   * [Magento Open Source](#opensource)

## Aggiornamento di Adobe Commerce {#upgrading-magento}

Se aggiorni Adobe Commerce su un’infrastruttura cloud, prova quanto segue per risolvere le dipendenze dei componenti in conflitto:

* Controllare le chiavi utilizzate per l&#39;aggiornamento. Le chiavi vengono generate dall’account e-mail corretto?
* Controlla le autorizzazioni e assicurati che corrispondano ai requisiti Magenti di aggiornamento. Revisione [Panoramica sull&#39;aggiornamento del Magento > Elenco di controllo per l&#39;aggiornamento e l&#39;aggiornamento > Autorizzazioni file system](https://devdocs.magento.com/guides/v2.3/comp-mgr/prereq/prereq_compman-checklist.html#perms) nella documentazione per gli sviluppatori.

## Incompatibilità con moduli di terze parti: {#incompatibility-third-party-modules}

Le dipendenze dei componenti in conflitto possono essere causate anche da moduli di terze parti che dipendono da componenti Commerce precedenti rispetto a quelli installati. Provare a eseguire le operazioni seguenti:

1. Nel precedente [esempio](#issue), il pacchetto installato magento/sample-data versione 0.74.0-beta15 non può essere aggiornato a 1.0.0-beta. Tuttavia, 0.74.0-beta15 può essere aggiornato a 0.74.0-beta16 (o altri). Modifica `composer.json` per apportare una di queste modifiche. In genere, le versioni richieste dal progetto vengono definite in `require` o `require-dev` dell&#39;oggetto in tale file JSON. A seconda delle opzioni fornite per le versioni dei pacchetti, è possibile specificare una versione specifica o un vincolo. Per informazioni generali su come utilizzare Compositore, se ti trovi nella nostra infrastruttura cloud, puoi fare riferimento a [Cloud per Adobe Commerce > Tecnologie e requisiti > Compositore](https://devdocs.magento.com/cloud/reference/cloud-composer.html#files) nella documentazione per gli sviluppatori. Se utilizzi Adobe Commerce on-premise, consulta [Adobe Commerce > Guida all’installazione > Installare Adobe Commerce utilizzando il Compositore](https://devdocs.magento.com/guides/v2.4/install-gde/composer.html) .
1. Ora prova il controllo di preparazione. Revisione [Panoramica dell’aggiornamento ad Adobe Commerce > Esegui Gestione moduli > Controllo preparazione passaggio 1](https://devdocs.magento.com/guides/v2.3/comp-mgr/module-man/compman-readiness.html) nella documentazione per gli sviluppatori.
1. Se il controllo di idoneità non riesce e viene visualizzato un messaggio di errore relativo al controllo di dipendenza di un altro componente, fare clic sui collegamenti seguenti a seconda che si utilizzi o meno [Adobe Commerce](#magento-commerce-magento-commerce-cloud) o [Magento Open Source](#opensource) per ulteriori passaggi per la risoluzione dei problemi.

## Adobe Commerce {#magento-commerce-magento-commerce-cloud}

1. Rivolgiti allo sviluppatore dell’estensione in modo che possa aiutarti. Le informazioni di contatto sono disponibili nella pagina da cui hai acquistato l’estensione, sulla Commerce Marketplace. Cerca **Contatta il venditore** nel pannello di destra. Tutti gli sviluppatori Commerce devono fornire una guida all’installazione e per l’utente quando pubblicano un’estensione su Marketplace. Entrambi sono disponibili sul lato destro della pagina di destinazione.
1. Se non ricevi una risposta dal venditore entro un periodo di tempo ragionevole, [contatta l’assistenza per il marketplace](mailto:commercemarketplacesupport@adobe.com) in modo che possiamo ricordare loro gli impegni per l&#39;assistenza clienti.

## Magento Open Source {#opensource}

Richiedi assistenza all&#39;indirizzo [il nostro forum principale](https://community.magento.com/) o [contattare un partner Adobe Commerce](https://magento.com/find-a-partner) che assiste nei problemi relativi ad Open Source.
