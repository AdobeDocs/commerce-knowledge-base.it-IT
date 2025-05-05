---
title: "ACSD-54376: eccezione nel carrello quando il prodotto viene rimosso da [!UICONTROL shared catalog]"
description: Applicare la patch ACSD-54376 per risolvere il problema di Adobe Commerce che causa un'eccezione nel carrello quando un prodotto viene rimosso da [!UICONTROL shared catalog] dopo essere stato aggiunto al carrello.
feature: Shopping Cart, B2B
role: Admin, Developer
exl-id: a1e5c084-532f-49e8-ab87-6674b44218e8
source-git-commit: 1cc565d5888e5a380c04879d9aced2c19e92c2e5
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-54376: eccezione nel carrello quando il prodotto viene rimosso da [!UICONTROL shared catalog]

La patch ACSD-54376 risolve il problema relativo a un&#39;eccezione nel carrello quando un prodotto viene rimosso da [!UICONTROL shared catalog] dopo essere stato aggiunto al carrello. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.41. L’ID della patch è ACSD-54376. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Eccezione nel carrello quando un prodotto viene rimosso da [!UICONTROL shared catalog] dopo essere stato aggiunto al carrello.

<u>Passaggi da riprodurre</u>:

1. Installare Adobe Commerce con B2B.
1. Abilita [!UICONTROL shared catalog].
1. Creare un prodotto e assegnarlo al [!UICONTROL shared catalog] predefinito.
1. Aggiungi un prodotto al carrello dalla vetrina.
1. Rimuovi il prodotto da [!UICONTROL shared catalog].
1. Passa alla pagina di pagamento utilizzando il menu a discesa mini-carrello.

<u>Risultati previsti</u>:

Le eccezioni vengono gestite e non visualizzate.

<u>Risultati effettivi</u>:

Nella pagina di pagamento viene visualizzata un&#39;eccezione non gestita.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
