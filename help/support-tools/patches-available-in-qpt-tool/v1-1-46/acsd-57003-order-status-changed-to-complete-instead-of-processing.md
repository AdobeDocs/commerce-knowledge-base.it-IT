---
title: "ACSD-57003: lo stato dell’ordine viene modificato in *Complete* invece di essere modificato in *Processing*"
description: Applica la patch ACSD-57003 per risolvere il problema Adobe Commerce, se lo stato dell’ordine cambia in *Complete* (Completato) invece di cambiare in *Processing* (Elaborazione).
feature: Orders, Invoices, Shipping/Delivery
role: Admin, Developer
exl-id: c3c59185-c447-46fa-b404-6c4a4a300315
source-git-commit: c5e94c6407394cd905ea470628d28db2c2c6c0ed
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-57003: lo stato dell’ordine viene modificato in *Completa* invece di passare a *Elaborazione*

La patch ACSD-57003 risolve il problema relativo alla modifica dello stato dell&#39;ordine in *Completa* invece di passare a *Elaborazione*. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.46. L’ID della patch è ACSD-57003. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Lo stato dell’ordine diventa *Completa* invece di passare a *Elaborazione* quando un ordine è parzialmente rimborsato e parzialmente spedito.

<u>Passaggi da riprodurre</u>:

1. Crea un ordine con due prodotti configurabili.
1. Fattura tutti gli articoli.
1. Spedire solo il primo articolo.
1. Rimborso/creazione di una nota di accredito solo per l&#39;articolo spedito (*primo elemento*).
1. Controlla lo stato dell’ordine.

<u>Risultati previsti</u>:

Lo stato dell’ordine deve essere nel _Elaborazione_ stato.

<u>Risultati effettivi</u>:

Lo stato dell’ordine cambia in *Completa* dopo la creazione di una nota di credito per l&#39;articolo spedito parzialmente.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
