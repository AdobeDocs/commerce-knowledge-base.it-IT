---
title: "ACSD-49849: l’e-mail del cliente è stata sostituita con l’e-mail PayPal"
description: Applica la patch ACSD-49849 per risolvere il problema Adobe Commerce in cui l’e-mail del cliente è stata sostituita con l’e-mail PayPal al momento di effettuare un ordine con PayPal Express tramite GraphQL.
exl-id: 826ea90a-ac10-43e8-aa88-bd69b152ded8
feature: Admin Workspace, Communications, Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-49849: l’e-mail del cliente viene sostituita con [!DNL PayPal] email

La patch ACSD-49849 risolve il problema della sostituzione dell’e-mail di un cliente con una [!DNL PayPal's] e-mail quando effettui un ordine con [!DNL PayPal Express] tramite GraphQL. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29. L’ID della patch è ACSD-49849. Il problema è stato risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.5-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’e-mail di un cliente viene sostituita con una [!DNL PayPal's] e-mail quando effettui un ordine con [!DNL PayPal Express] tramite GraphQL.

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Payments]**.
1. Abilita e configura [!DNL PayPal Express] e imposta **[!UICONTROL Payment Action]** = **[!UICONTROL Sale]**.
1. Vai a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** e creare un prodotto semplice.
1. Completa il pagamento tramite GraphQL. Per ulteriori informazioni, consulta [Tutorial sull’estrazione di GraphQL](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/) nella documentazione di Adobe Commerce Developer.
1. Utilizzare [!DNL PayPal Express] come metodo di pagamento.
1. Nota l’e-mail utilizzata nel passaggio in cui [configurare l’e-mail per il carrello](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/set-email-address/) nella documentazione di Adobe Commerce Developer.
1. Dopo aver effettuato l’ordine, passa all’amministratore Adobe Commerce e controlla l’e-mail nell’ordine creato.

<u>Risultati previsti</u>:

L’e-mail è la stessa impostata durante il pagamento.

<u>Risultati effettivi</u>:

L’e-mail impostata durante l’estrazione viene sostituita dall’e-mail impostata in [!DNL PayPal] account.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
