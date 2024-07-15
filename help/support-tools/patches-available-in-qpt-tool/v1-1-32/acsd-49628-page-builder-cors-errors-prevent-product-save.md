---
title: "ACSD-49628: [!DNL Page Builder] Gli errori CORS impediscono il salvataggio del prodotto"
description: Applica la patch ACSD-49628 per risolvere il problema di Adobe Commerce in cui gli errori  [!DNL Page Builder] CORS impediscono il salvataggio del prodotto.
exl-id: c6e2f0b3-aea0-4caf-8b69-9644b38c909c
feature: Categories, Page Builder, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-49628: [!DNL Page Builder] errori CORS impediscono il salvataggio del prodotto

La patch ACSD-49628 risolve il problema in cui [!DNL Page Builder] errori CORS impediscono a un amministratore di salvare un prodotto. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.32. L’ID della patch è ACSD-49628. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

[!DNL Page Builder] errori CORS impediscono il salvataggio di un prodotto.

<u>Passaggi da riprodurre</u>:

1. Accedi come amministratore.
1. Crea un ruolo utente con le seguenti autorizzazioni:

   * **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Products]**.
   * **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Categories]**.

1. Non aggiungere autorizzazioni *[!UICONTROL Content]*.
1. Crea un altro utente amministratore e assegna a questo utente i ruoli creati in precedenza.
1. Crea un prodotto e disconnettiti.
1. Accedi come secondo amministratore.
1. Prova a modificare e salvare il prodotto.

<u>Risultati previsti</u>:

Il secondo amministratore è in grado di salvare il prodotto, ma il pulsante **[!UICONTROL Edit with Page Builder]** non viene visualizzato all&#39;amministratore senza alcuna autorizzazione *[!UICONTROL Content]*.

<u>Risultati effettivi</u>:

Il secondo amministratore non è in grado di salvare il prodotto a causa di più errori di [!DNL Page Builder].

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
