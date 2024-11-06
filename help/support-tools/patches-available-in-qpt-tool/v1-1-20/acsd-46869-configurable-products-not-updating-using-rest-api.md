---
title: "ACSD-46869: i prodotti configurabili non vengono aggiornati utilizzando l’API REST al momento del pagamento"
description: La patch ACSD-46869 risolve il problema che impedisce l’aggiornamento dei prodotti configurabili tramite l’API REST al momento del pagamento. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20. L’ID della patch è ACSD-46869. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.
exl-id: d1bac489-f0f3-4b50-bc48-86c844230da7
feature: REST, Checkout, Configuration, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# ACSD-46869: i prodotti configurabili non vengono aggiornati utilizzando l’API REST al momento del pagamento

La patch ACSD-46869 risolve il problema che impedisce l’aggiornamento dei prodotti configurabili tramite l’API REST al momento del pagamento. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20. L’ID della patch è ACSD-46869. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL QPT] pagina di destinazione](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I prodotti configurabili non vengono aggiornati utilizzando l’API REST durante il pagamento.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto configurabile con attributi di colore e dimensioni.
1. Selezionare **[!UICONTROL Options]** e aggiungere il prodotto al carrello.
1. Vai a **[!UICONTROL Checkout]**, aggiorna le dimensioni più volte tranne che per la quantità, quindi controlla la richiesta e la risposta.
1. Quando si aggiornano le dimensioni, viene visualizzata la seguente risposta.

```REST API
{"extension_attributes":{"configurable_item_options":[
{"option_id":"960","option_value":25083},
{"option_id":"801","option_value":177}
]}}
```

<u>Risultati previsti</u>:

Il valore viene aggiornato in base alle modifiche.

<u>Risultati effettivi</u>:

`option_value` non è aggiornato, quindi quando l&#39;ordine viene effettuato, ha il valore di dimensione precedente.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tools] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida dello strumento Patch di qualità.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) nella nostra Knowledge Base di supporto.

Per informazioni sulle altre patch disponibili in [!DNL QPT], fare riferimento a [Patch disponibili in [!DNL QPT]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida dello strumento Patch di qualità.
