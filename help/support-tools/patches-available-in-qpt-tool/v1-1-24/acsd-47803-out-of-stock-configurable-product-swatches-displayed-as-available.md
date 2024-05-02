---
title: "ACSD-47803: campioni di prodotto configurabili esauriti visualizzati come disponibili"
description: Applica la patch ACSD-47803 per risolvere il problema di Adobe Commerce, se i campioni di prodotto configurabili esauriti vengono visualizzati come disponibili.
exl-id: 28b3f378-a790-4af6-9627-5bd8571523fd
feature: Configuration, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-47803: campioni di prodotto configurabili esauriti visualizzati come disponibili

La patch ACSD-47803 risolve il problema relativo alla disponibilità di campioni di prodotto configurabili esauriti. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24. L’ID della patch è ACSD-47803. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I campioni di prodotto configurabili esauriti vengono visualizzati in base alla disponibilità.

<u>Passaggi da riprodurre</u>:

>[!NOTE]
>
>I passaggi seguenti si riferiscono a dati di esempio.

1. In [!UICONTROL Commerce] Amministratore, vai a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** e imposta **[!UICONTROL Display Out of Stock Products]** a *Sì*.
1. Anche in questo caso, dall’amministratore, passa a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** e modificare un prodotto configurabile nella pagina di modifica del prodotto (ad esempio, &quot;WB04&quot; SKU, se si utilizzano dati di esempio):
   * Per una delle varianti di configurazione, impostare la quantità su *0* ad esempio &quot;WB04-M-Purple&quot;).
1. Ora apri il prodotto configurabile sulla vetrina.
1. Seleziona la dimensione del prodotto per la variante configurabile con zero azioni (cioè &quot;M&quot;).

<u>Risultati previsti</u>:

Le opzioni esaurite sono disabilitate e contrassegnate come [!UICONTROL Out of Stock].

<u>Risultati effettivi</u>:

Tutti i campioni colore sono abilitati, anche quello [!UICONTROL Out of Stock].

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
