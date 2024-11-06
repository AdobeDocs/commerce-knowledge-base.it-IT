---
title: L’Extension Manager non mostra estensioni in Adobe Commerce 2.3.x
description: Questo articolo fornisce una soluzione alternativa per le estensioni mancanti nell’Extension Manager per amministratori in Adobe Commerce 2.3.x dopo l’acquisto di estensioni tramite Commerce Marketplace.
exl-id: bed8506d-39b9-449a-891b-466d214a0fe8
feature: Extensions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# L’Extension Manager non mostra estensioni in Adobe Commerce 2.3.x

Questo articolo fornisce una soluzione alternativa per le estensioni mancanti nell’Extension Manager per amministratori in Adobe Commerce 2.3.x dopo l’acquisto di estensioni tramite Commerce Marketplace.

## Prodotti e versioni interessati

* Versione Adobe Commerce (tutti i metodi di distribuzione) 2.3.x

## Problema

Quando acquisti estensioni tramite Commerce Marketplace, non puoi installarle utilizzando l’Extension Manager di Adobe Commerce di base. Quando aggiungi i tasti di accesso e esegui la sincronizzazione con il Marketplace, nell’Extension Manager non viene visualizzata alcuna estensione.

La **soluzione** per il problema consiste nell&#39;utilizzare l&#39;installazione della riga di comando di Adobe Commerce, come illustrato nella [Installazione generale di CLI](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/extensions) nella documentazione per gli sviluppatori.

<u>Passaggi da riprodurre</u>:

1. Acquista un’estensione tramite Commerce Marketplace.
1. Aggiungi i tasti di accesso dell’estensione e sincronizzali con il Marketplace.
1. Vai alla sezione Extension Manager dell’Admin.

<u>Risultato previsto</u>:

L’estensione viene visualizzata nella sezione Extension Manager di Commerce Admin.

<u>Risultato effettivo</u>:

**Nella sezione Extension Manager dell&#39;amministratore Commerce non è presente alcuna estensione, simile all&#39;immagine seguente:**


![KB-607_Image_1.png](assets/KB-607_Image_1.png)

## Soluzione alternativa

Utilizzare l&#39;installazione della riga di comando di Adobe Commerce come illustrato in [Installazione generale di CLI](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/extensions) nella documentazione per gli sviluppatori.
