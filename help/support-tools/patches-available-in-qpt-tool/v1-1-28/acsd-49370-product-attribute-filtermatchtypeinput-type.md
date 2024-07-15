---
title: '"ACSD-49370: l’attributo del prodotto ha il tipo "FilterMatchTypeInput" nello schema di GraphQL"'
description: Applica la patch ACSD-49370 per risolvere il problema di Adobe Commerce in cui l’attributo del prodotto ha un tipo "FilterMatchTypeInput" nello schema GraphQL.
exl-id: 132eee3a-30b0-4810-b2f0-0d05d0a9f009
feature: Admin Workspace, Attributes, GraphQL, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-49370: l&#39;attributo del prodotto ha il tipo `FilterMatchTypeInput` nello schema GraphQL

La patch ACSD-49370 risolve il problema se l&#39;attributo del prodotto ha un tipo `FilterMatchTypeInput` nello schema GraphQL. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28. L’ID della patch è ACSD-49370. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;attributo di prodotto ha un tipo `FilterMatchTypeInput` nello schema GraphQL.

<u>Passaggi da riprodurre</u>:

1. Creare l&#39;attributo di prodotto *Date and Time*.

   * [!UICONTROL Type]: [!UICONTROL DateTime]
   * [!UICONTROL Default Label]: [!UICONTROL Date Time]
   * [!UICONTROL Use in Search]: [!UICONTROL Yes]
   * [!UICONTROL Visible in Advanced Search]: [!UICONTROL Yes]

1. Eseguire una query sulla documentazione *API GQL* per la definizione del tipo `ProductAttributeFilterInput`.
1. Osserva il tipo di input per l’attributo creato.

<u>Risultati previsti</u>:

L&#39;attributo *Date Time* mostra il tipo di input del filtro `FilterRangeTypeInput`.

<u>Risultati effettivi</u>:

L&#39;attributo *Date Time* mostra il tipo di input del filtro `FilterMatchInputType`.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
