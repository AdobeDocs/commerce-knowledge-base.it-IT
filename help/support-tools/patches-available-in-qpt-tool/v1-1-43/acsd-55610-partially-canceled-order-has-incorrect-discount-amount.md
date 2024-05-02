---
title: "ACSD-55610: l’ordine parzialmente annullato presenta un importo di sconto errato"
description: Applicare la patch ACSD-55610 per risolvere il problema Adobe Commerce in cui un ordine parzialmente annullato presenta un importo di sconto errato.
feature: Invoices, Orders, Price Rules, Shopping Cart
role: Admin, Developer
exl-id: f4cca4fa-dc04-4c86-9176-c648b1d0e732
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-55610: l&#39;importo dello sconto dell&#39;ordine parzialmente annullato non è corretto

La patch ACSD-55610 risolve il problema relativo a un ordine parzialmente annullato con un importo di sconto errato. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.43. L’ID della patch è ACSD-55610. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Un ordine annullato parzialmente presenta un importo di sconto errato.

<u>Passaggi da riprodurre</u>:

1. Crea una regola per il prezzo del carrello.

   * *[!UICONTROL Rule Name]*: *Vendita invernale*
   * *[!UICONTROL Active]* = *Sì*
   * *[!UICONTROL Websites]* = *Sito Web principale*
   * Scegliere tutti i gruppi di clienti.
   * Seleziona un coupon specifico.
   * *[!UICONTROL Coupon Code]*: *INVERNO10*
   * *[!UICONTROL Conditions]*: *[!UICONTROL If ALL of these conditions are TRUE]*: *Subtotale (escl. Imposta) è uguale o maggiore di 75*
   * Applica *[!UICONTROL Percent of product price discount]*.
   * *[!UICONTROL Discount Amount]*: *10*
   * *[!UICONTROL Discard subsequent rules]*: *Sì*

1. Crea tre prodotti con prezzi impostati su 100.
1. Aggiungi i tre prodotti al carrello.
1. Applica il coupon.
1. Effettua l’ordine.
1. Fatturare un articolo dell&#39;ordine e spedirlo.
1. Annulla gli altri due elementi.
1. Controlla la `base_discount_canceled` colonna.

<u>Risultati previsti</u>:

Importo sconto in `base_discount_cancelled` rifletta correttamente.

<u>Risultati effettivi</u>:

Il `base_discount_cancelled` non è corretto.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
