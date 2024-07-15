---
title: "ACSD-56790: l'opzione **[!UICONTROL move out of stock to bottom]** non funziona durante l'ordinamento dei prodotti in  [!DNL Visual Merchandiser]"
description: Applica la patch ACSD-56790 per risolvere il problema di Adobe Commerce, in cui l’opzione ESAURIMENTO SCORTE non funziona durante l’ordinamento dei prodotti in Visual Merchandiser.
feature: Products, Categories
role: Admin, Developer
exl-id: a0c61696-a12d-4c1a-a061-e2f17f38e1f4
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# ACSD-56790: l&#39;opzione **[!UICONTROL move out of stock to bottom]** non funziona durante l&#39;ordinamento dei prodotti in [!DNL Visual Merchandiser]

La patch di ACSD-56790 risolve il problema che impedisce il funzionamento dell&#39;opzione di spostamento tra le scorte in esaurimento durante l&#39;ordinamento dei prodotti in [!DNL Visual Merchandiser]. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44. L’ID della patch è ACSD-56790. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;opzione **[!UICONTROL move out of stock to bottom]** non funziona durante l&#39;ordinamento dei prodotti in [!DNL Visual Merchandiser]

<u>Passaggi da riprodurre</u>:

1. Installa Adobe Commerce.
1. Vai a **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** e crea i seguenti attributi.
1. Crea un nuovo sito Web: **Non principale**.
1. Crea un **archivio non principale** in questo nuovo sito Web.
1. Crea due store:

   * Primo nell&#39;**archivio siti Web principale**.
   * Secondo nell&#39;**archivio non principale**.

1. Creare due origini:
   * Lettere.
   * Numeri.

1. Creazione di due scorte:
   * Primo principale - canali di vendita: sito web principale - fonti assegnate: lettere.
   * Secondo non principale - canali di vendita: non principale - fonti assegnate: numeri.

1. Crea tre prodotti semplici su entrambi i siti web, tutti nella categoria Predefinito, tutti assegnati a entrambe le origini:

   * ProductA - Qtà *10* in lettere, Qtà *0* in numeri.
   * Prodotto1 - Qtà *0* in lettere, Qtà *10* in numeri.
   * ProductA1 - Qtà *10* in lettere, Qtà *10* in numeri.

1. Vai a **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** e seleziona **[!UICONTROL Default category]**.
1. Cambia l&#39;ambito in **First**.
1. Espandi la voce Prodotti nella sezione Categoria.
1. Selezionare l&#39;ordinamento come: **[!UICONTROL move out of stock to bottom]**

<u>Risultati previsti</u>:

L&#39;elenco dei prodotti con **esauriti** è stato spostato in basso.

<u>Risultati effettivi</u>:

Impossibile caricare i prodotti. Una pagina viene reindirizzata al dashboard di amministrazione con il messaggio di errore: `Invalid security or form key. Please refresh the page`

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
