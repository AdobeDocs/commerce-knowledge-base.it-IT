---
title: L’Extension Manager non mostra estensioni in Adobe Commerce 2.3.x
description: Questo articolo fornisce una soluzione alternativa per le estensioni mancanti nell’Extension Manager per amministratori in Adobe Commerce 2.3.x dopo l’acquisto di estensioni tramite Commerci Marketplace.
exl-id: bed8506d-39b9-449a-891b-466d214a0fe8
feature: Extensions
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# L’Extension Manager non mostra estensioni in Adobe Commerce 2.3.x

Questo articolo fornisce una soluzione alternativa per le estensioni mancanti nell’Extension Manager per amministratori in Adobe Commerce 2.3.x dopo l’acquisto di estensioni tramite Commerci Marketplace.

## Prodotti e versioni interessati

* Versione Adobe Commerce (tutti i metodi di distribuzione) 2.3.x

## Problema

Quando acquisti estensioni tramite Commerci Marketplace, non puoi installarle utilizzando l’Extension Manager di Adobe Commerce di base. Quando aggiungi i tasti di accesso e esegui la sincronizzazione con il Marketplace, nell’Extension Manager non viene visualizzata alcuna estensione.

Il **Soluzione alternativa** il problema consiste nell’utilizzare l’installazione della riga di comando di Adobe Commerce come mostrato nella [Installazione generale di CLI](https://devdocs.magento.com/extensions/install/) nella documentazione per gli sviluppatori.

<u>Passaggi da riprodurre</u>:

1. Acquista un’estensione tramite Commerci Marketplace.
1. Aggiungi i tasti di accesso dell’estensione e sincronizzali con il Marketplace.
1. Vai alla sezione Extension Manager dell’Admin.

<u>Risultato previsto</u>:

L’estensione viene visualizzata nella sezione Extension Manager di Commerce Admin.

<u>Risultato effettivo</u>:

**Nella sezione Extension Manager di Commerce Admin non viene visualizzata alcuna estensione simile a quella riportata di seguito:**


![KB-607_Image_1.png](assets/KB-607_Image_1.png)

## Soluzione alternativa

Utilizza l’installazione della riga di comando di Adobe Commerce come mostrato nella [Installazione generale di CLI](https://devdocs.magento.com/extensions/install/) nella documentazione per gli sviluppatori.
