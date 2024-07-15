---
title: "Adobe Commerce 2.4.2-p1: nota fattura con valore errato"
description: Questo articolo descrive un problema noto di Adobe Commerce 2.4.2-p1 in cui viene generata una nota di fattura con valore errato quando il gruppo di clienti viene modificato durante la creazione dell’ordine. Questo problema è stato risolto nella versione 2.4.3.
exl-id: bde90251-625f-4c9d-8e5a-9a2019656125
feature: Customer Service, Invoices
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# Adobe Commerce 2.4.2-p1: nota fattura con valore errato

Questo articolo descrive un problema noto di Adobe Commerce 2.4.2-p1 in cui viene generata una nota di fattura con valore errato quando il gruppo di clienti viene modificato durante la creazione dell’ordine. Questo problema è stato risolto nella versione 2.4.3.

## Prodotti e versioni interessati

* Adobe Commerce on-premise 2.4.2-p1
* Adobe Commerce sull’infrastruttura cloud 2.4.2-p1

## Problema

Quando il gruppo di clienti viene modificato al momento della creazione dell&#39;ordine, la fattura viene generata con una nota di fattura errata.

<u>Passaggi da riprodurre</u>:

1. Crea un **Account cliente di prova** e aggiungilo al **Gruppo clienti vendita al dettaglio**.
1. Crea un **nuovo ordine** per il cliente di prova, aggiungi **prodotto** e **indirizzo**.
1. Selezionare **Metodo di spedizione**.
1. Nella sezione **Informazioni account**, cambia il gruppo clienti da **Rivenditore** a **Pubblica amministrazione**.
1. Fai clic su **Inserisci ordine**.
1. Fare clic su **Fattura** > **Invia fattura**.

<u>Risultati previsti</u>:

La nota seguente deve essere visualizzata nella sezione **Note per questo ordine**: &quot;Fattura vertice inviata correttamente. Importo: $0,00.&quot;

<u>Risultati effettivi</u>:

La nota seguente viene visualizzata nella sezione **Note per questo ordine**: &quot;Fattura vertice inviata correttamente. Importo: $3,23.&quot;

## Soluzione

Questo problema è stato risolto nella versione 2.4.3.
