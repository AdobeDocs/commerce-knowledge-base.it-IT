---
title: 'Adobe Commerce 2.4.2-p1: nota fattura con valore errato'
description: Questo articolo descrive un problema noto di Adobe Commerce 2.4.2-p1 in cui viene generata una nota di fattura con valore errato quando il gruppo di clienti viene modificato durante la creazione dell’ordine. Questo problema è stato risolto nella versione 2.4.3.
exl-id: bde90251-625f-4c9d-8e5a-9a2019656125
feature: Customer Service, Invoices
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 591c578b-908e-5b79-a9d3-931dfe60c24c
    internal-label: Invoices
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
subfeature_v2:
  - id: deedbb4d-f1b7-58ea-a34a-de1f481f9d4c
    internal-label: Customer Service
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '229'
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
1. Nella sezione **Informazioni account**, cambia il gruppo clienti da **Retailer** a **Amministrazione**.
1. Fai clic su **Inserisci ordine**.
1. Fare clic su **Fattura** > **Invia fattura**.

<u>Risultati previsti</u>:

La nota seguente deve essere visualizzata nella sezione **Note per questo ordine**: &quot;Fattura vertice inviata correttamente. Importo: $0,00.&quot;

<u>Risultati effettivi</u>:

La nota seguente viene visualizzata nella sezione **Note per questo ordine**: &quot;Fattura vertice inviata correttamente. Importo: $3,23.&quot;

## Soluzione

Questo problema è stato risolto nella versione 2.4.3.
