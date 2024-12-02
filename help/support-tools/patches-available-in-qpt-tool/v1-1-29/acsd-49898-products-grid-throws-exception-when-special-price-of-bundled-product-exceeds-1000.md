---
title: 'ACSD-49898: la griglia Prodotti genera un''eccezione'
description: Applica la patch ACSD-49898 per risolvere il problema di Adobe Commerce, a causa del quale la griglia prodotti genera un’eccezione quando un prodotto in bundle ha un prezzo speciale che supera i 1000.
exl-id: 16a0ec90-7577-46ef-aeb3-a7e9658cf64b
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-49898: la griglia Prodotti genera un&#39;eccezione

La patch ACSD-49898 risolve il problema relativo alla griglia dei prodotti che genera un&#39;eccezione quando un prodotto in bundle ha un prezzo speciale che supera i 1000. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29. L’ID della patch è ACSD-49898. Il problema è stato risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.5-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La griglia Prodotti genera un’eccezione quando un prodotto in bundle ha un prezzo speciale che supera i 1000. Il problema riguarda l’utilizzo di virgole invece dei punti per i numeri decimali in determinate lingue.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto in bundle.
1. Impostare il prezzo speciale su 9999; salvare e chiudere.
1. Passa a **[!UICONTROL Catalog]** > **[!UICONTROL Products]**

>[!NOTE]
>
>Se non è visibile, cerca il codice SKU del prodotto in bundle.

<u>Risultati previsti</u>:

* L&#39;utente è in grado di filtrare/visualizzare il prodotto in bundle con il prezzo speciale.
* Il prezzo speciale è indicato come percentuale per i prodotti raggruppati e come prezzo per altri tipi di prodotto.

<u>Risultati effettivi</u>:

Viene generato il seguente errore: *È stato rilevato un valore non numerico*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
