---
title: "ACSD-49464: Fatture, spedizioni e note di accredito non spostate dall'archivio"
description: Applicare la patch ACSD-49464 per risolvere il problema Adobe Commerce, in cui fatture, spedizioni e note di accredito non vengono spostate dall'archivio quando l'ID ordine è diverso.
exl-id: 845f9878-5f7e-4e58-8f8a-b02af17b3f11
feature: Admin Workspace, Invoices, Orders, Returns, Shipping/Delivery
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# ACSD-49464: Fatture, spedizioni e note di accredito non spostate dall&#39;archivio

La patch di ACSD-49464 risolve il problema che impedisce lo spostamento di fatture, spedizioni e note di credito dall&#39;archivio quando l&#39;ID ordine è diverso. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29. L’ID della patch è ACSD-49464. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le fatture, le spedizioni e le note di accredito non vengono spostate dall&#39;archivio quando l&#39;ID ordine è diverso.

<u>Passaggi da riprodurre</u>:

1. Abilita l&#39;archiviazione di ordini, fatture, spedizioni e note di accredito.
1. Crea e completa un ordine, incluse spedizione, fattura e nota di accredito.
1. Verificare che gli ID di spedizione, fattura e nota di accredito non corrispondano al numero dell&#39;ordine.
1. Sposta l’ordine nell’archivio.
1. Ripristinare l&#39;ordine archiviato in Order Management.
1. Verifica i dettagli di fattura, spedizione e nota di accredito nella rispettiva [!UICONTROL Invoice], [!UICONTROL Shipping], e [!UICONTROL Credit Memo] pagine della griglia.

<u>Risultati previsti</u>:

I record correlati originali vengono ripristinati quando l&#39;ordine viene spostato dall&#39;elenco di archiviazione alla gestione degli ordini.

<u>Risultati effettivi</u>:

* Nessun record per le note di spedizione, fattura e credito se tutti gli ID sono diversi.
* Se l&#39;ordine e i record correlati hanno lo stesso ID, i record vengono restituiti.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
