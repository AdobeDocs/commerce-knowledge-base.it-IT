---
title: "ACSD-51683: l’opzione personalizzabile non può essere aggiunta al carrello utilizzando GraphQL"
description: Applica la patch ACSD-51683 per risolvere il problema di Adobe Commerce, se non è possibile aggiungere l’opzione personalizzabile al carrello utilizzando GraphQL.
feature: GraphQL
role: Admin
exl-id: 4de0d8b7-714e-4bbf-8a0d-bb6e0c3aae55
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-51683: l’opzione personalizzabile non può essere aggiunta al carrello utilizzando GraphQL

La patch ACSD-51683 risolve il problema che impediva l’aggiunta dell’opzione personalizzabile al carrello con GraphQL. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.35. L’ID della patch è ACSD-51683. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Non è possibile aggiungere l’opzione personalizzabile al carrello utilizzando GraphQL.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto semplice con un&#39;opzione **Campo di testo** personalizzabile.
1. [Aggiungi al carrello](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/add-product-to-cart/) il prodotto creato con l&#39;opzione personalizzabile richiesta tramite GraphQL.
1. Invia la richiesta di GraphQL [carrello](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/queries/cart/) per controllare il prodotto e i relativi dettagli nel carrello.

<u>Risultati previsti</u>

La sezione `Customizable_options` nella risposta di GraphQL contiene i dati forniti durante l&#39;aggiunta del prodotto al carrello.

<u>Risultati effettivi</u>

La sezione `Customizable_options` nella risposta di GraphQL è vuota.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
