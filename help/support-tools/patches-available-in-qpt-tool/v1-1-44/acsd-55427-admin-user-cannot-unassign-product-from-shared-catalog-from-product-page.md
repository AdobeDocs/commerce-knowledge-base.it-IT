---
title: 'ACSD-55427: un amministratore non può annullare l''assegnazione di un prodotto da **[!UICONTROL Product in Shared Catalogs]** nella pagina del prodotto'
description: Applicare la patch ACSD-55427 per risolvere il problema di Adobe Commerce che impedisce l'annullamento dell'assegnazione di un prodotto da **[!UICONTROL Product in Shared Catalogs]**.
feature: Products, B2B
role: Admin, Developer
exl-id: 1e08def1-07f6-42e0-b600-9f0bfdd6477a
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-55427: un amministratore non può annullare l&#39;assegnazione di un prodotto da **[!UICONTROL Product in Shared Catalogs]** nella pagina del prodotto

La patch ACSD-55427 risolve il problema che impediva di annullare l&#39;assegnazione di un prodotto da **[!UICONTROL Product in Shared Catalogs]** nella pagina del prodotto nel catalogo di Commerce Admin. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44. L’ID della patch è ACSD-55427. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Non puoi annullare l&#39;assegnazione di un prodotto da **[!UICONTROL Product in Shared Catalogs]** nella pagina del prodotto nel catalogo in Commerce Admin.

<u>Passaggi da riprodurre</u>:

Prerequisiti: Adobe Commerce installato con B2B e **[!UICONTROL Shared Catalogs]** abilitati.
1. Crea un prodotto.
1. Passa alla dashboard del catalogo condiviso e apri il catalogo condiviso predefinito.
1. Assegnazione del prodotto al catalogo predefinito e impostazione di un prezzo inferiore al prezzo del prodotto.
1. Salva il catalogo condiviso.
1. Eseguire [!UICONTROL CRON] per aggiornare i consumer/indicizzatori.
1. Aprire il prodotto e rimuoverlo dalla sezione **[!UICONTROL Product in Shared Catalogs]**.

<u>Risultati previsti</u>:

Il prodotto deve essere rimosso dalla sezione **[!UICONTROL Product in Shared Catalogs]**.

<u>Risultati effettivi</u>:

Il prodotto è ancora visualizzato nella sezione **[!UICONTROL Product in Shared Catalogs]**.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
