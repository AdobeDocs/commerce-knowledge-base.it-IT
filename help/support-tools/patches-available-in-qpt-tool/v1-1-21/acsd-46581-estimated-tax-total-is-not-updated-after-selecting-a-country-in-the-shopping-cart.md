---
title: "ACSD-46581: il totale fiscale stimato non viene aggiornato dopo aver selezionato un paese nel carrello"
description: Applica la patch ACSD-46581 per risolvere il problema Adobe Commerce, in cui l’aliquota non viene aggiornata dopo il passaggio dal paese al carrello.
exl-id: 17334f7b-e5a2-4091-8196-eff80875c003
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# ACSD-46581: il totale imposte stimato non viene aggiornato dopo aver selezionato un paese nel carrello

Questa patch ACSD-46581 risolve il problema in cui l’aliquota fiscale non viene aggiornata dopo il passaggio dal paese al carrello. Viene aggiornato solo dopo aver selezionato il metodo di spedizione. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21. L’ID della patch è ACSD-46581. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.1-p1

**Compatibile con le versioni di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’aliquota non viene aggiornata dopo il passaggio da un paese all’altro nel carrello.

<u>Passaggi da riprodurre</u>:

1. Nell&#39;amministrazione di Adobe Commerce, vai a **[!UICONTROL Stores]** > **[!UICONTROL Tax Zone and Rates]**.
1. Crea una nuova aliquota per **[!UICONTROL Country]** = _Stati Uniti_, **[!UICONTROL State]** = _*_, **[!UICONTROL Rate]** = _8.25_.
1. Crea una nuova aliquota per **[!UICONTROL Country]** = _India_, **[!UICONTROL State]** = _*_, **[!UICONTROL Rate]** = _10_.
1. Creare una regola fiscale con entrambe le aliquote per Stati Uniti e India.
1. Vai a **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Shipping Methods]** e abilita più di un metodo di spedizione (_Tariffa fissa_ e _Spedizione gratuita_, ad esempio).
1. Creare un prodotto semplice con la classe fiscale **[!UICONTROL Taxable Goods]**.
1. Aggiungi il prodotto al carrello sulla vetrina.
1. Apri il carrello e controlla l’importo dell’imposta.
1. Vengono applicate le impostazioni di imposta predefinite per gli Stati Uniti e l&#39;imposta viene calcolata in base a un&#39;aliquota dell&#39;8,25%.
1. Passa all&#39;India.

<u>Risultati previsti</u>:

L&#39;importo dell&#39;imposta è cambiato al 10% quando si cambia il paese in India.

<u>Risultati effettivi</u>:

L’importo dell’imposta rimane invariato nella sezione totale del carrello.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, vedere [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
