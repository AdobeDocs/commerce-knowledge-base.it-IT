---
title: Applicare una patch per continuare a offrire DHL come corriere
description: Questo articolo fornisce una patch che consente ai commercianti che utilizzano Adobe Commerce 2.4.4 e versioni precedenti di continuare a offrire la spedizione DHL, dopo che lo schema DHL 6.0 diventerà obsoleto alla fine di luglio - settembre 2022.
exl-id: 4350e83a-495b-41b4-a526-dae5923e9d41
feature: Orders, Shipping/Delivery, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# Applicare una patch per continuare a offrire DHL come corriere


## Prodotti e versioni interessati

* Adobe Commerce 2.4.4 e versioni precedenti, tutti i metodi di distribuzione.

## Problema

DHL sta introducendo una versione dello schema 6.2 e sta rendendo obsoleta la versione 6.0 entro la fine di luglio - settembre 2022. Adobe Commerce 2.4.4 e la precedente integrazione DHL supportano solo la versione 6.0.

## Soluzione

Adobe Commerce 2.4.5, la cui versione è prevista per agosto 2022, conterrà l’integrazione aggiornata con DHL utilizzando lo schema versione 6.2. Fino al rilascio della nuova versione (o nel caso in cui si decida di non effettuare l&#39;aggiornamento), si consiglia di applicare la patch AC-3022, implementando il supporto schema DHL versione 6.2, per continuare a offrire spedizioni DHL nel proprio negozio dopo la deprecazione.

## Patch

L&#39;ID patch è AC-3022 disponibile nella versione 1.1.16 dello strumento Quality Patches Tool.
Per informazioni su come utilizzare e installare le patch, consulta l&#39;articolo [Strumento Patch di qualità (QPT) > Utilizzo](https://devdocs.magento.com/quality-patches/usage.html) nella documentazione per gli sviluppatori.

La patch è applicabile alle seguenti versioni di Adobe Commerce:

* 2,4,0 - 2,4,4-p1
* 2.3.7.

## Lettura correlata

* [Vettori di spedizione > DHL](https://docs.magento.com/user-guide/shipping/dhl.html) nella nostra guida utente
* [Metodi di consegna](https://docs.magento.com/user-guide/configuration/sales/delivery-methods.html) nella guida utente
