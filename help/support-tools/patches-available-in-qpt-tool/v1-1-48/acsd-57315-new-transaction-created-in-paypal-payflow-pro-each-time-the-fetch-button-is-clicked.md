---
title: 'ACSD-57315: viene creata una nuova transazione in [!DNL PayPal Payflow Pro] ogni volta che si fa clic sul pulsante Fetch'
description: Applica la patch ACSD-57315 per risolvere il problema Adobe Commerce relativo alla creazione di una nuova transazione in [!DNL PayPal Payflow Pro] ogni volta che si fa clic sul pulsante Recupera nella schermata Visualizza transazione in [!UICONTROL Admin].
feature: Payments
role: Admin, Developer
exl-id: bcc7467d-09f9-4235-9f9f-46d3034567b8
source-git-commit: d7ace1f20defb01105d4a241f971b06fca052215
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-57315: viene creata una nuova transazione in [!DNL PayPal Payflow Pro] ogni volta che si fa clic sul pulsante Fetch

La patch ACSD-57315 risolve il problema relativo alla creazione di una nuova transazione in [!DNL PayPal Payflow Pro] ogni volta che si fa clic sul pulsante Recupera nella schermata Visualizza transazione in [!UICONTROL Admin]. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.48. L’ID della patch è ACSD-57315. Il problema è pianificato per essere risolto in Adobe Commerce 2.5.0.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.6-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

In [!DNL PayPal Payflow Pro] viene creata una nuova transazione ogni volta che si fa clic sul pulsante Fetch nella schermata Visualizza transazione in [!UICONTROL Admin].

<u>Passaggi da riprodurre</u>:

1. Configura [!DNL PayPal Payflow Pro].
1. Impostare il metodo di transazione su *[!UICONTROL Sale]*.
1. Effettua un ordine utilizzando *Carta di credito*.
1. Apri la transazione da [!UICONTROL Admin].
1. Fare clic sul pulsante **[!UICONTROL Fetch]**.
1. Controlla l&#39;account [!DNL PayPal] per le transazioni relative all&#39;ordine effettuato.

<u>Risultati previsti</u>:

Non viene creata una nuova transazione di pagamento.

<u>Risultati effettivi</u>:

Viene creata una nuova transazione di pagamento per un ordine già pagato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
