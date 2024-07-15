---
title: Adobe Commerce 2.4.1 e 2.3.6 creano un hotfix con pulsante account disabilitato
description: Questo articolo fornisce un hotfix per il problema quando si ha difficoltà a creare un nuovo account dopo aver inserito un valore errato in qualsiasi campo del modulo. Ad esempio, quando inserisci un indirizzo e-mail in un formato errato o lasci vuoti i campi nome o cognome o non inserisci un valore che soddisfi i requisiti della password. Nelle versioni Q1 verrà inclusa una correzione permanente (2.4.2, 2.4.1-p1 e 2.3.6-p1).
exl-id: e6e65ede-8156-4e2b-b369-b18395bb3dbf
feature: Customer Service
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# Adobe Commerce 2.4.1 e 2.3.6 creano un hotfix con pulsante account disabilitato

Questo articolo fornisce un hotfix per il problema quando si ha difficoltà a creare un nuovo account dopo aver inserito un valore errato in qualsiasi campo del modulo. Ad esempio, quando inserisci un indirizzo e-mail in un formato errato o lasci vuoti i campi nome o cognome o non inserisci un valore che soddisfi i requisiti della password. Nelle versioni Q1 verrà inclusa una correzione permanente (2.4.2, 2.4.1-p1 e 2.3.6-p1).

## Problema

Il pulsante **Crea account** nella pagina **Crea nuovo account** rimane disabilitato se un acquirente ha immesso dati non validi. In questo modo si evita che gli acquirenti tentino nuovamente di creare un account dopo aver commesso un errore.

<u>Passaggi da riprodurre</u>:

1. Vai a **Crea nuovo account cliente**.
1. Compila i campi modulo. Nel campo **Password** immettere valori che non soddisfano i requisiti della password. Ad esempio:
   * Le password nei campi **Password** e **Conferma password** non corrispondono.
   * Le password nei campi **Password** e **Conferma password** non sono sufficientemente lunghe.
1. Fare clic sul pulsante **Crea account**.

<u>Risultati previsti</u>:

* **Creare un account** deve rimanere attivo/abilitato.
* L’utente deve essere in grado di creare un nuovo account.

<u>Risultati effettivi</u>:

* **Il pulsante Crea account** rimane disattivato anche dopo aver compilato tutti i campi obbligatori con dati validi/corretti.
* Il cliente non è in grado di creare un nuovo account.

## Patch

La patch è allegata a questo articolo. Per scaricarlo, scorrere verso il basso fino alla fine dell&#39;articolo e fare clic sul nome del file oppure sul collegamento seguente: [Scarica MC-38509-compositore.patch](assets/MC-38509-composer.patch.zip)

## Versioni compatibili di Adobe Commerce:

La patch è stata creata per:

* Adobe Commerce sull’infrastruttura cloud 2.3.6 e 2.4.1.
* Adobe Commerce on-premise 2.3.6 e 2.4.1

La patch non è compatibile con altre versioni ed edizioni di Adobe Commerce.

## Come applicare il cerotto

Per istruzioni, vedere [Come applicare una patch del compositore fornita dall&#39;Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).

## Lettura correlata

* [Adobe Commerce GitHub > Con l&#39;invio di un modulo account di creazione non valido il pulsante di invio rimane disattivato](https://github.com/magento/magento2/issues/30513)
* [Guida utente di Adobe Commerce > Guida introduttiva > Creazione di un account](https://docs.magento.com/user-guide/magento/magento-account-create.html)
