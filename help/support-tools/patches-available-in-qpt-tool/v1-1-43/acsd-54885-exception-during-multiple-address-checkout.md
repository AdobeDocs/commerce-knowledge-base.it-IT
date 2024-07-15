---
title: "ACSD-54885: eccezione durante l’estrazione di più indirizzi quando l’amministratore effettua l’accesso come cliente"
description: Applicare la patch ACSD-54885 per risolvere il problema Adobe Commerce in cui si verifica un errore durante l'estrazione di più indirizzi quando l'amministratore utilizza la funzionalità *[!UICONTROL Login as Customer]*.
feature: Checkout
role: Admin, Developer
exl-id: 524ec96b-1465-4673-9fbe-1a9c086b7e87
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-54885: eccezione durante l’estrazione di più indirizzi quando l’amministratore accede come cliente

La patch ACSD-54885 risolve il problema relativo a un errore durante l&#39;estrazione di più indirizzi quando l&#39;amministratore utilizza la funzionalità *[!UICONTROL Login as Customer]*. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43. L’ID della patch è ACSD-54885. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Errore durante l&#39;estrazione di più indirizzi quando l&#39;amministratore utilizza la funzionalità *[!UICONTROL Login as Customer]*.

<u>Passaggi da riprodurre</u>:

1. Assicurarsi che *[!UICONTROL Login as Customer]* sia abilitato. Vai a **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configurations]** > **[!UICONTROL Advanced]** > **[!UICONTROL Admin]** > **[!UICONTROL Admin Actions]** > **[!UICONTROL Logging]** > **[!UICONTROL Login as Customer]**.
1. Crea un prodotto semplice.
1. Crea un nuovo account cliente con un indirizzo.
1. Vai al conto cliente nel backend:

   * Passare alla scheda **[!UICONTROL Account Information]** e impostare *[!UICONTROL Allow remote shopping assistance]* = *Sì*.
   * Fare clic su **[!UICONTROL Login as Customer]**.

1. Aggiungere il prodotto al carrello e passare a *[!UICONTROL Checkout with multiple addresses]*.
1. Aggiorna la quantità del prodotto.
1. Prova a tornare al carrello.

<u>Risultati previsti</u>:

Puoi aggiornare il carrello e utilizzare il checkout di più indirizzi.

<u>Risultati effettivi</u>:

Quando torni al carrello, ricevi il seguente errore.

```PHP
report.CRITICAL: Error: Call to a member function getCustomer() on null in magento2ee/app/code/Magento/LoginAsCustomerLogging/Observer/LogUpdateQtyObserver.php:88
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
