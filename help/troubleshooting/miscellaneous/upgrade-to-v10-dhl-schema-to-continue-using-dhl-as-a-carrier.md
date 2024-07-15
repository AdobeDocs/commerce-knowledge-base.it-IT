---
title: Effettua l’aggiornamento allo schema DHL v10 per continuare a offrire la spedizione DHL
description: Questo articolo fornisce una soluzione per consentire ai commercianti di continuare a offrire la spedizione DHL dopo che lo schema DHL 6.2 è diventato obsoleto nel dicembre 2022, aggiornando lo schema 10.0 o applicando la patch AC-3023.
exl-id: eed83713-2d6a-4360-bfa1-bebd4d604f2f
feature: Orders, Shipping/Delivery, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# Effettua l’aggiornamento alla versione 10.0 dello schema DHL per continuare a offrire la spedizione DHL

Questo articolo fornisce una soluzione per consentire ai commercianti di continuare a offrire la spedizione DHL dopo che la versione dello schema DHL 6.2 sarà obsoleta alla fine di dicembre 2022.

## Prodotti e versioni interessati

* Adobe Commerce 2.4.5 e versioni precedenti, tutti i metodi di distribuzione.

## Problema

Nell&#39;agosto 2022 è stato rilasciato l&#39;[aggiornamento dello schema DHL versione 6.2. insieme a una patch di correzione](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/adobe-commerce-dhl-upgrade-patch.html) per consentire ai commercianti di continuare a offrire la spedizione DHL. DHL sta introducendo nuovamente uno schema più recente - versione 10.0 - a ottobre 2022 e la versione precedente (schema 6.2) diventerà obsoleta alla fine di dicembre 2022. Adobe Commerce 2.4.5 e la precedente integrazione DHL supportano solo la versione 6.2.

## Soluzione

Adobe Commerce 2.4.5-p1 e 2.4.4-p2, rilasciati a ottobre 2022, contengono il nuovo schema DHL versione 10.0. Pertanto, i commercianti che aggiornano a 2.4.5-p1 e 2.4.4-p2 non devono fare nulla per continuare a offrire le spedizioni DHL. Invitiamo tutti i commercianti ad effettuare l’aggiornamento a 2.4.5-p1 e 2.4.4-p2 prima che lo schema DHL 6.2. venga dichiarato obsoleto alla fine di dicembre 2022.

I commercianti che non desiderano effettuare l’aggiornamento a 2.4.5-p1 e 2.4.4-p2 dovranno applicare una patch di correzione se desiderano continuare a offrire la spedizione DHL dopo dicembre 2022.

## Patch

L&#39;ID patch è AC-3023 ed è disponibile nella versione 1.1.21 di [!DNL Quality Patches Tool].

Fare riferimento ai seguenti collegamenti per informazioni su come utilizzare [!DNL Quality Patches Tool] e installare le patch in base ai metodi di distribuzione utilizzati:

* Adobe Commerce on-premise e Magento Open Source: [Strumenti per le patch di qualità > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in Adobe Experience League.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

**La patch è applicabile alle seguenti versioni di Adobe Commerce (tutti i metodi di distribuzione):**

* 2.3.7, 2.4.0, 2.4.1, 2.4.2, 2.4.3, 2.4.3-p2, 2.4.3-p3, 2.4.4

## Collegamenti utili

* [[!DNL Quality Patches Tool] > Note sulla versione](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/release-notes.html) in Adobe Experience League.

* [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in Adobe Experience League.

## Lettura correlata

* [Applica una patch per continuare a offrire DHL come corriere](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/adobe-commerce-dhl-upgrade-patch.html) nella nostra knowledge base di supporto.

* [Vettori di spedizione > DHL](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/delivery/shipping-carriers/dhl.html) nella guida utente.
* [Riferimento configurazione > Vendite > Metodi di consegna](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/delivery-methods.html) nella guida utente.
