---
title: Nella colonna dello stato Adobe Commerce manca il file CSV dei prodotti esportati
description: Questo articolo fornisce una soluzione al problema quando non è possibile individuare la colonna di stato nel file CSV contenente i prodotti esportati.
exl-id: 3cbe1e6c-fc73-4331-add7-1ebcb28a4580
feature: Data Import/Export, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Nella colonna dello stato Adobe Commerce manca il file CSV dei prodotti esportati

Questo articolo fornisce una soluzione al problema quando non è possibile individuare la colonna di stato (ovvero, che indica se il prodotto è abilitato o disabilitato) nel file CSV contenente i prodotti esportati. Lo stato del prodotto è indicato dalla colonna [!UICONTROL product_online].

## Prodotti e versioni interessati

Adobe Commerce (tutti i metodi di distribuzione) tutte le [versioni supportate](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problema

Impossibile individuare la colonna [!UICONTROL status] nel file CSV contenente i prodotti esportati. Ad esempio, puoi esportare un file CSV di tutti gli SKU con il relativo stato, ma nella tabella manca la colonna [!UICONTROL status].

<u>Passaggi da riprodurre:</u>

1. In Adobe Commerce Admin, selezionare **[!UICONTROL System]**, in **[!UICONTROL Data Transfer]** selezionare **[!UICONTROL Export]**.
1. Nella sezione **[!UICONTROL Export Settings]**, selezionare nell&#39;elenco a discesa **[!UICONTROL Entity Type]** **[!UICONTROL Products]**.
1. Cerca **[!UICONTROL status]**, elencato in **[!UICONTROL Attribute Code]**. Il codice attributo è presente nell&#39;elenco degli attributi disponibili (**[!UICONTROL Enable Product]**).
1. Fai clic su **[!UICONTROL Export]**.

<u>Risultato previsto:</u>

Nel file CSV appena esportato viene visualizzata una colonna con etichetta [!UICONTROL status].

<u>Risultato effettivo:</u>

Nel file csv esportato non è presente una colonna con etichetta [!UICONTROL status].

## Causa

L’attributo di stato del prodotto è stato rinominato nel file CSV. Ora è la colonna [!UICONTROL product_online].

## Soluzione

1. Selezionare **[!UICONTROL System]**, in **[!UICONTROL Data Transfer]** selezionare **[!UICONTROL Import]**.
1. Fare clic su **[!UICONTROL Download Sample File]**.
1. Puoi visualizzare la colonna [!UICONTROL product_online] nel file CSV.

## Lettura correlata

* [Utilizzo dei file CSV](https://docs.magento.com/user-guide/system/data-csv.html) nella guida utente.
* [Riferimento per gli attributi di esportazione del prodotto](https://docs.magento.com/user-guide/system/data-attributes-product.html) nella guida utente.
