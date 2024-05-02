---
title: "ACSD-54680: impossibile elaborare il preventivo B2B per un prodotto con più origini assegnate"
description: Applica la patch ACSD-54680 per risolvere il problema di Adobe Commerce che impedisce l’elaborazione del preventivo B2B per un prodotto con più origini assegnate.
feature: B2B
role: Admin, Developer
exl-id: 4d05714c-d32d-46f3-b857-81704c9e96cd
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# ACSD-54680: impossibile elaborare il preventivo B2B per un prodotto con più origini assegnate.

La patch ACSD-54680 risolve il problema che impedisce l&#39;elaborazione del preventivo B2B per un prodotto con più origini assegnate. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.40. L’ID della patch è ACSD-54680. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.5-p5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Impossibile elaborare il preventivo B2B per un prodotto con più origini assegnate.

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Sources]** e creare due nuove sorgenti: **Sorgente 1** e **Sorgente 2**.
1. Vai a **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Stocks]** e crea un nuovo Stock: **Magazzino A**, assegnarlo al sito Web principale e assegnare **Sorgente 1** e **Sorgente 2** ad esso.
1. Creare un prodotto semplice, assegnare **Sorgente 1** e **Sorgente 2**, e impostare Qtà = *2* per ogni sorgente. (la quantità vendibile del prodotto deve essere *4* di conseguenza).
1. Crea un account aziendale.
1. Vai a **[!UICONTROL Storefront]** e accedere all&#39;account aziendale.
1. Aggiungi il prodotto semplice al carrello con qtà = *4*.
1. Apri *[!UICONTROL Shopping cart]* e fai clic su **[!UICONTROL Request a quote]** pulsante.
1. Aggiungere un commento e il nome dell&#39;offerta e fare clic su **[!UICONTROL Send a Request]** pulsante.
1. Vai a **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**.
1. Apre il preventivo inviato di recente.

<u>Risultati previsti</u>:

Gli articoli citati contengono il prodotto ordinato.

<u>Risultati effettivi</u>:

La sezione pagina articoli citati è vuota e non è possibile elaborare l&#39;offerta.
`var/log/system.log` contiene

```
report.CRITICAL: TypeError: number_format() expects parameter 1 to be float, null given in .../vendor/magento/module-negotiable-quote/Model/QuoteUpdatesInfo.php:232
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
