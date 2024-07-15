---
title: "ACSD-51497: impossibile ordinare la pagina del catalogo in base all’attributo personalizzato di tipo A discesa"
description: Applica la patch ACSD-51497 per risolvere il problema di Adobe Commerce, a causa del quale un cliente non può ordinare una pagina di catalogo in base all’attributo personalizzato del tipo a discesa.
feature: Attributes, Cache, Catalog Management, Categories
role: Developer
exl-id: 60a4f375-9b9a-4026-9dc7-d9f847a75656
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# ACSD-51497: impossibile ordinare la pagina del catalogo in base all&#39;attributo personalizzato di tipo *Elenco a discesa*

La patch ACSD-51497 risolve il problema che impediva al cliente di ordinare una pagina di catalogo in base a un attributo personalizzato di tipo *Elenco a discesa*. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33. L’ID della patch è ACSD-51497. Il problema è stato risolto in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.3.7-p4, 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Un cliente non è in grado di ordinare una pagina di catalogo in base a un attributo personalizzato di tipo *Elenco a discesa*.

<u>Passaggi da riprodurre</u>

1. Crea circa sei semplici prodotti e assegnali a una singola categoria.
1. Crea un attributo di prodotto per aggiungerlo come opzione di ordinamento nelle pagine di elenco.

   * Vai a **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Add New Attribute]**.
   * Nella scheda **[!UICONTROL Properties]**, impostare quanto segue:

      * *[!UICONTROL Default Label]* = *test*
      * *[!UICONTROL Catalog Input Type]* per proprietario archivio = *Elenco a discesa*
      * *[!UICONTROL Options]*:

         * *primo*
         * *secondo*
         * *terzo*
         * *quarto*

   * Nella scheda **[!UICONTROL Storefront Properties]**, impostare quanto segue:

      * *[!UICONTROL Used for sorting in product listing]* = *Sì*
      * Lascia tutte le altre opzioni come *Predefinito*.

1. Assegna l&#39;attributo *test* all&#39;attributo *Default* impostato in **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**.
1. Configurare i prodotti in modo che abbiano valori di attributo *test*.

   * SKU: s00001, prova: quarta
   * SKU: s00002, prova: terzo
   * SKU: s00003, test: second
   * SKU: s00004, test: first
   * SKU: s00005, prova: quarta
   * SKU: s00006, prova: terzo

1. Reindicizzare e cancellare la cache.
1. Vai alla categoria nella vetrina.
1. Ordina in base all&#39;attributo *test*.

<u>Risultati previsti</u>:

I prodotti sono ordinati in base all&#39;attributo *test*.

<u>Risultati effettivi</u>:

I prodotti non sono ordinati dall&#39;attributo *test*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
