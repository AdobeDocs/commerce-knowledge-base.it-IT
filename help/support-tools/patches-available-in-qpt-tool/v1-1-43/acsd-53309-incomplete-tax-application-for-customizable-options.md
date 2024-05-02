---
title: '"ACSD-53309: applicazione fiscale incompleta per opzioni personalizzabili e [!UICONTROL Regular Price] label'''
description: Applica la patch ACSD-53309 per risolvere il problema di Adobe Commerce in cui l’imposta non è completamente applicata nel "[!UICONTROL Regular Price]etichetta ' quando è selezionata un’opzione personalizzabile.
feature: Taxes, Shipping/Delivery
role: Admin, Developer
exl-id: de9b151e-6f92-4231-9e9f-4818c2961782
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-53309: applicazione fiscale incompleta per le opzioni personalizzabili e &#39;[!UICONTROL Regular Price]etichetta &#39;

La patch ACSD-53309 risolve il problema della mancata completa applicazione dell&#39;imposta nel[!UICONTROL Regular Price]etichetta &#39; quando è selezionata un’opzione personalizzabile. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43. L’ID della patch è ACSD-53309. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’imposta non si riflette completamente in &quot;[!UICONTROL Regular Price]Etichetta &#39; quando si sceglie un&#39;opzione personalizzabile.

<u>Passaggi da riprodurre</u>:

1. Accedi al pannello di amministrazione.
1. Accedi a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Tax]** per configurare le impostazioni relative alle imposte.

   * [!UICONTROL Tax Classes]:

      * [!UICONTROL Tax Class for Shipping] = [!UICONTROL Taxable Goods]
      * [!UICONTROL Tax Class for Gift Options] = [!UICONTROL Taxable Goods]

   * [!UICONTROL Calculation Settings]:

      * [!UICONTROL Catalog Prices] = [!UICONTROL Including Tax]
      * [!UICONTROL Shipping Prices] = [!UICONTROL Including Tax]
      * [!UICONTROL Apply Discount On Prices] = [!UICONTROL Including Tax]

   * [!UICONTROL Default Tax Destination Calculation]:

      * [!UICONTROL Default Post Code] = *

   * [!UICONTROL Price Display Settings]:

      * [!UICONTROL Display Product Prices In Catalog] = [!UICONTROL Including Tax]
      * [!UICONTROL Display Shipping Prices] = [!UICONTROL Including Tax]

   * [!UICONTROL Shopping Cart Display Settings]:

      * [!UICONTROL Display Prices] = [!UICONTROL Including Tax]
      * [!UICONTROL Display Subtotal] = [!UICONTROL Including Tax]
      * [!UICONTROL Display Shipping Amount] = [!UICONTROL Including Tax]

1. Imposta **[!UICONTROL Shipping Settings]** > **[!UICONTROL Origin]** > **[!UICONTROL Country]** = *Regno Unito*.

1. Crea quanto segue *[!UICONTROL Tax Rate]* e *[!UICONTROL Tax Rules]*:

   * [!UICONTROL Country] = Stati Uniti
   * [!UICONTROL Zip Code] = *
   * [!UICONTROL State] = *
   * [!UICONTROL Rate] = 20%
1. Crea un prodotto semplice e imposta quanto segue:
   * [!UICONTROL Price = 110]
   * [!UICONTROL Special Price = 100]
   * Nell’elenco a discesa, imposta il tipo su opzione personalizzata con prezzo impostato al 15%
1. Vai alla pagina del prodotto per l’elemento semplice realizzato nella vetrina.
1. Scegli l’opzione personalizzata creata, *15%*.

<u>Risultati previsti</u>:

* L’opzione personalizzata selezionata prevede l’applicazione di un’imposta del 20%.
* &#39;[!UICONTROL Regular Price]&#39; = 151,80.

<u>Risultati effettivi</u>:

* L&#39;imposta del 20% non viene applicata all&#39;opzione personalizzata selezionata.
* &#39;[!UICONTROL Regular Price]&#39; = 148,50.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
