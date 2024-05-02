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

1. Creare un **Verifica account cliente** e aggiungerlo al **Gruppo di clienti al dettaglio**.
1. Creare un **Nuovo ordine** per il cliente di prova, aggiungi **Prodotto** e **Indirizzo**.
1. Seleziona **Metodo di spedizione**.
1. In **Informazioni account** sezione, cambia gruppo di clienti da **Rivenditore** a **Pubblica amministrazione**.
1. Clic **Inserisci ordine**.
1. Clic **Fattura** > **Sottometti fattura**.

<u>Risultati previsti</u>:

La nota seguente dovrebbe essere visualizzata sotto **Note per questo ordine**  sezione: &quot;Fattura vertice inviata correttamente. Importo: $0,00.&quot;

<u>Risultati effettivi</u>:

La nota seguente viene visualizzata sotto **Note per questo ordine** sezione: &quot;Fattura vertice inviata correttamente. Importo: $3,23.&quot;

## Soluzione

Questo problema è stato risolto nella versione 2.4.3.
