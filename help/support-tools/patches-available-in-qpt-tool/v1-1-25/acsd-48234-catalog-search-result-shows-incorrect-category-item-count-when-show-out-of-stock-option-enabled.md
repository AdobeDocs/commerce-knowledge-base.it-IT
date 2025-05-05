---
title: 'ACSD-48234: risultato della ricerca catalogo errato nel conteggio degli elementi della categoria quando [!UICONTROL Display Out of Stock Products] è abilitato'
description: Applicare la patch ACSD-48234 per risolvere il problema di Adobe Commerce, in cui il risultato della ricerca nel catalogo mostra un conteggio di elementi di categoria errato quando l'opzione [!UICONTROL Display Out of Stock Products] è abilitata.
exl-id: 8e70fe73-d550-4e11-b25e-84955e136d12
feature: Admin Workspace, Categories, Catalog Management, Orders, Products, Search
role: Admin
source-git-commit: 3eeb86c2644f8a04ddcf5e205bc400d2ca9969af
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-48234: il risultato della ricerca nel catalogo indica che il conteggio degli elementi di categoria **[!UICONTROL Display Out of Stock Products]** è abilitato non corretto

La patch di ACSD-48234 risolve il problema relativo alla visualizzazione di un numero di elementi di categoria non corretto da parte del risultato della ricerca nel catalogo quando l&#39;opzione **[!UICONTROL Display Out of Stock Products]** è abilitata. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25. L’ID della patch è ACSD-48234. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.


## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.5-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il risultato della ricerca nel catalogo mostra un conteggio degli elementi di categoria errato quando l&#39;opzione **[!UICONTROL Display Out of Stock Products]** è abilitata.

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** e apri l&#39;attributo **[!UICONTROL color]**.
1. Aggiungi due opzioni, ad esempio arancione e verde. Salva l’attributo.
1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]** e aggiungi l&#39;attributo **[!UICONTROL color]** al set di attributi **[!UICONTROL Default]**.
1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL CATALOG]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** e imposta **[!UICONTROL Display Out of Stock Products]** su _Sì_.
1. Crea la categoria &quot;cat1&quot;.
1. Crea due prodotti:
   1. Nome: prod1, Colore: arancione, Categorie: cat1.
   1. Nome: prod2, Colore: verde, Categorie: cat1.
1. Apri la categoria cat1 nella vetrina.
1. Selezionare il colore arancione nella navigazione a livelli.

<u>Risultati previsti</u>:

Viene visualizzato solo il prodotto prod1.

<u>Risultati effettivi</u>:

Vengono visualizzati sia i prodotti prod1 che prod2.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
