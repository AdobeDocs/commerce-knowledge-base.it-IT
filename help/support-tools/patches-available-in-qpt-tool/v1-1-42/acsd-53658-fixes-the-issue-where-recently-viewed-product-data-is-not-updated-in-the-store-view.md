---
title: 'ACSD-53658: **[!UICONTROL Recently Viewed Product]** dati non aggiornati correttamente nella visualizzazione archivio'
description: Applicare la patch ACSD-53658 per risolvere il problema di Adobe Commerce per cui i dati **[!UICONTROL Recently Viewed Product]** non vengono aggiornati correttamente nella visualizzazione archivio.
feature: CMS, Personalization
role: Admin, Developer
exl-id: 4086dcee-37e5-4393-9048-ce19a2d248e9
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-53658: i dati **[!UICONTROL Recently Viewed Product]** non vengono aggiornati correttamente nella visualizzazione archivio

La patch ACSD-53658 risolve il problema che causa l&#39;aggiornamento non corretto dei dati di **[!UICONTROL Recently Viewed Product]** nella visualizzazione archivio. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42. L’ID della patch è ACSD-53658. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I dati di **[!UICONTROL Recently Viewed Product]** non sono aggiornati correttamente nella visualizzazione archivio.

<u>Passaggi da riprodurre</u>:

1. Accedi al pannello di amministrazione.
1. Crea una seconda visualizzazione store per il sito Web predefinito.
1. Crea un prodotto semplice.
1. Imposta un nome di prodotto diverso per la nuova visualizzazione store.
1. Crea un widget **[!UICONTROL Recently Viewed Product]**.
1. Configura questo widget per visualizzarlo nella home page.
1. Apri la pagina del prodotto sullo Storefront dalla visualizzazione predefinita dello store.
1. Aprire la home page.
1. Utilizzando il commutatore store, passare alla seconda visualizzazione store.

<u>Risultati previsti</u>:

Il nome del prodotto viene aggiornato nel widget.

<u>Risultati effettivi</u>:

Il nome del prodotto non viene aggiornato nel widget.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
