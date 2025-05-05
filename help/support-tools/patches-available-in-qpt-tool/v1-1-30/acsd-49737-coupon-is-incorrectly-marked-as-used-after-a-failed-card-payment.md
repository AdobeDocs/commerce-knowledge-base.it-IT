---
title: 'ACSD-49737: il coupon è erroneamente contrassegnato come utilizzato dopo un pagamento con carta non riuscito'
description: Applicare la patch ACSD-49737 per risolvere il problema Adobe Commerce in cui il coupon viene erroneamente contrassegnato come utilizzato dopo un pagamento con carta non riuscito.
exl-id: 77b5ec9c-3c4c-4da3-ba7e-8be3ccea04d0
feature: Orders, Payments
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-49737: il coupon è contrassegnato in modo errato come *usato* dopo un pagamento con carta non riuscito

La patch ACSD-49737 risolve il problema relativo al fatto che il coupon viene erroneamente contrassegnato come *usato* dopo un pagamento con carta non riuscito. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30. L’ID della patch è ACSD-49737. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1-p1 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il coupon è contrassegnato in modo errato come *usato* dopo un pagamento con carta non riuscito.

<u>Prerequisiti</u>:

1. Configurare il metodo **[!UICONTROL Braintree sandbox payment]**.
1. Assicurati che il consumer [*sales.rule.update.coupon.usage*](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/message-queues/consumers.html?lang=it) sia configurato e in esecuzione.

<u>Passaggi da riprodurre</u>:

1. Crea un **[!UICONTROL Cart Price Rule]** con codici coupon generati automaticamente.
1. Accedi come cliente.
1. Aggiungi prodotti al carrello.
1. Applica un codice coupon generato automaticamente.
1. Provare a effettuare un ordine con un pagamento non riuscito.
1. Controllare l&#39;utilizzo del coupon in **[!UICONTROL Cart Price Rule]** nella scheda **[!UICONTROL Manage Coupon Codes]**.

<u>Risultati previsti</u>:

Il coupon non deve essere contrassegnato come *usato* se il pagamento non è riuscito.

<u>Risultati effettivi</u>:

* Il codice coupon indica: utilizzato: *Sì*, ore utilizzate: *1*
* Il codice coupon è valido solo per un singolo utilizzo.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Passaggi aggiuntivi necessari dopo l&#39;installazione della patch

Questa sezione è facoltativa; potrebbero essere necessari alcuni passaggi dopo l’applicazione della patch per risolvere il problema. 

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
