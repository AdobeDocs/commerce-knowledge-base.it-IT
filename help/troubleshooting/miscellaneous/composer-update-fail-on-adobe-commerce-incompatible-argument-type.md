---
title: "Aggiornamento del compositore non riuscito in Adobe Commerce: tipo di argomento non compatibile"
description: Questo articolo fornisce una soluzione per i casi in cui la distribuzione è bloccata a causa di un problema con la compilazione del codice. Questo problema è causato da una nuova versione della dipendenza di symfony/console (4.4.27, 4.4.28).
exl-id: ba2dd229-29f6-43e2-9467-8bd1bf59e6ef
feature: Console
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# Aggiornamento del compositore non riuscito in Adobe Commerce: tipo di argomento non compatibile

>[!NOTE]
>
>Questo problema è stato risolto con l’ultima versione di symfony 4.4.29.

Questo articolo fornisce una soluzione per i casi in cui la distribuzione è bloccata a causa di un problema con la compilazione del codice. Questo problema è causato da una nuova versione della dipendenza di symfony/console (4.4.27, 4.4.28).

## Prodotti e versioni interessati

* Adobe Commerce (tutti i metodi di distribuzione) e Magento Open Source:
   * 2.4.0, 2.4.0-p1, 2.4.1, 2.4.1-p1, 2.4.2, 2.4.2-p1, 2.4.2-p2, 2.4.3
   * 2.3.5, 2.3.5-p1, 2.3.5-p2, 2.3.6, 2.3.6-p1, 2.3.7, 2.3.7-p1
* dipendenza da symfony/console (4.4.27, 4.4.28).

## Problema

Una nuova versione della dipendenza di symfony/console (4.4.27, 4.4.28) sta causando un errore nel processo di compilazione della dipendenza.

<u>Passaggi da riprodurre</u>:

Quando si installa o si aggiorna Adobe Commerce o si esegue l’aggiornamento del compositore, l’esecuzione non riesce e viene visualizzato il seguente messaggio di errore:
*Tipo di argomento non compatibile: tipo richiesto: int. Tipo effettivo: stringa*

## Causa

Il problema è causato dall’incompatibilità del codice core di Adobe Commerce con la più recente dipendenza &quot;symfony/console&quot; rilasciata nelle versioni 4.4.27 e 4.4.28.

## Soluzione

Il problema verrà risolto automaticamente una volta rilasciata la nuova versione di symfony/console 4.2.29 (prevista per agosto 2021).

**Correzione in Adobe Commerce on-premise:**

Adobe Commerce on-premise 2.4.x

Eseguire il comando seguente in CLI/Terminal:

``composer require symfony/console:">=4.4.0 <4.4.27 || ~4.4.29"``

Tutti i commercianti on-premise Adobe Commerce versione 2.3.5 devono eseguire il seguente comando CLI:

``composer require symfony/console:"~4.1.0||~4.2.0||~4.3.0||>=4.4.0 <4.4.27 || ~4.4.29"``

**Correzione in Adobe Commerce sull&#39;infrastruttura cloud:**

Esegui i comandi di cui sopra o effettua l’aggiornamento alla versione più recente degli strumenti ECE (strumenti ece: 2002.1.7), che sarà disponibile giovedì 29 luglio. Per i passaggi, consulta [Cloud for Adobe Commerce > Update ece-tools version](https://devdocs.magento.com/cloud/project/ece-tools-update.html) nella nostra documentazione per sviluppatori.

La correzione completa verrà rilasciata in Adobe Commerce (tutti i metodi di distribuzione) 2.4.4.

## Lettura correlata

* Github: [2021-07-27 Aggiornamento Compositore Tipo di argomento incompatibile: Tipo richiesto: int. Tipo effettivo: stringa](https://github.com/magento/magento2/issues/33595)
