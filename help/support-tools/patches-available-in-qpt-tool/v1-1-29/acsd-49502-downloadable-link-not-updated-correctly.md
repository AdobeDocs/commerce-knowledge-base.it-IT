---
title: "ACSD-49502: collegamento scaricabile non aggiornato correttamente dopo [!DNL staging] aggiornamento"
description: Applica la patch ACSD-49502 per risolvere il problema di Adobe Commerce per cui il collegamento scaricabile non viene aggiornato correttamente dopo l'applicazione di un aggiornamento  [!DNL staging]  al prodotto scaricabile.
exl-id: 9e7f0c06-4b7d-42c4-8ec7-cdeefd7e8a08
feature: Staging
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-49502: collegamento scaricabile non aggiornato correttamente dopo l&#39;aggiornamento di [!DNL staging]

La patch ACSD-49502 risolve il problema che impedisce l&#39;aggiornamento corretto del collegamento scaricabile dopo l&#39;applicazione di un aggiornamento [!DNL staging] al prodotto scaricabile. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29. L’ID della patch è ACSD-49502. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il collegamento scaricabile non viene aggiornato correttamente dopo l&#39;applicazione di un aggiornamento [!DNL staging] al prodotto scaricabile.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto scaricabile con i collegamenti.
1. Crea un account cliente e accedi.
1. Aggiungi il prodotto scaricabile al carrello dalla vetrina.
1. In **[!UICONTROL Admin]**, pianifica un nuovo aggiornamento per il prodotto scaricabile e lascia che l&#39;aggiornamento pianificato venga completato.
1. Completa l’ordine nella vetrina.

<u>Risultati previsti</u>:

I collegamenti scaricabili vengono mantenuti quando si utilizzano aggiornamenti pianificati mentre i prodotti aggiunti in precedenza si trovano nel carrello.

<u>Risultati effettivi</u>:

Nei collegamenti scaricabili mancano sia le pagine di visualizzazione *[!UICONTROL My Account]* ([!UICONTROL My Downloadable Products]) del cliente che le pagine di visualizzazione degli ordini in **[!UICONTROL Admin]**.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
