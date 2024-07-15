---
title: "ACSD-48587: il widget del prodotto non funziona con SKU contenenti caratteri HTML"
description: Applica la patch ACSD-48587 per risolvere il problema di Adobe Commerce, in cui i caratteri speciali HTML nelle regole di corrispondenza dei widget dei prodotti impediscono la visualizzazione dei prodotti corrispondenti.
exl-id: 9f8f436c-f3ef-4510-a941-12f701e7524e
feature: Admin Workspace, CMS, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-48587: il widget prodotto non funziona con SKU contenenti caratteri HTML

La patch ACSD-48587 risolve il problema in cui i caratteri speciali HTML nelle regole di corrispondenza dei widget dei prodotti impediscono loro di visualizzare i prodotti corrispondenti. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26. L’ID della patch è ACSD-48587. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il widget prodotto non funziona con SKU contenenti simboli *&quot;&amp;&quot;*.

<u>Passaggi da riprodurre</u>:

1. Creare un prodotto contenente *&quot;&amp;&quot;* nello SKU (ad esempio, s000&amp;01).
1. Modifica il contenuto di una pagina CMS nel *Page Builder*.
1. Aggiungi un widget prodotti.
1. Modificare il widget e impostare **[!UICONTROL Select Products by]** = **[!UICONTROL SKU]**.
1. Immettere lo SKU che contiene *&quot;&amp;&quot;* nel campo SKU prodotto.
1. Salva il contenuto e la pagina CMS.
1. Controlla il contenuto della *pagina CMS* per l&#39;*anteprima Page Builder* e la vetrina del prodotto.

<u>Risultati previsti</u>:

Il prodotto con *&quot;&amp;&quot;* nello SKU viene visualizzato nell&#39;anteprima di Page Builder e nella vetrina.

<u>Risultati effettivi</u>:

Il prodotto con *&quot;&amp;&quot;* nello SKU non viene visualizzato nell&#39;anteprima di Page Builder.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
