---
title: "ACSD-49737: il coupon è erroneamente contrassegnato come utilizzato dopo un pagamento con carta non riuscito"
description: Applicare la patch ACSD-49737 per risolvere il problema Adobe Commerce in cui il coupon viene erroneamente contrassegnato come utilizzato dopo un pagamento con carta non riuscito.
exl-id: 77b5ec9c-3c4c-4da3-ba7e-8be3ccea04d0
feature: Orders, Payments
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-49737: il coupon è erroneamente contrassegnato come *utilizzato* dopo un pagamento con carta non riuscito

La patch ACSD-49737 risolve il problema se il coupon è erroneamente contrassegnato come *utilizzato* dopo un pagamento con carta non riuscito. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30. L’ID della patch è ACSD-49737. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1-p1 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il coupon è contrassegnato in modo errato come *utilizzato* dopo un pagamento con carta non riuscito.

<u>Prerequisiti</u>:

1. Configurare **[!UICONTROL Braintree sandbox payment]** metodo.
1. Assicurati che le [*sales.rule.update.coupon.usage*](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/message-queues/consumers.html?lang=en) il consumer è configurato e operativo.

<u>Passaggi da riprodurre</u>:

1. Creare un **[!UICONTROL Cart Price Rule]** con codici coupon generati automaticamente.
1. Accedi come cliente.
1. Aggiungi prodotti al carrello.
1. Applica un codice coupon generato automaticamente.
1. Provare a effettuare un ordine con un pagamento non riuscito.
1. Controlla l’utilizzo del coupon in **[!UICONTROL Cart Price Rule]** sotto **[!UICONTROL Manage Coupon Codes]** scheda.

<u>Risultati previsti</u>:

Il coupon non deve essere contrassegnato come *utilizzato* se il pagamento non è riuscito.

<u>Risultati effettivi</u>:

* Il codice coupon dice - Usato: *Sì*, Tempi di utilizzo: *1*
* Il codice coupon è valido solo per un singolo utilizzo.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Passaggi aggiuntivi necessari dopo l&#39;installazione della patch

Questa sezione è facoltativa; potrebbero essere necessari alcuni passaggi dopo l’applicazione della patch per risolvere il problema. 

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
