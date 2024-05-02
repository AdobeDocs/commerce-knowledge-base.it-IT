---
title: "ACSD-52736 [!UICONTROL Cart Price Rule] non funziona come previsto"
description: Applicare la patch ACSD-52736 per risolvere il problema Adobe Commerce in cui [!UICONTROL Cart Price Rule] che include i requisiti per la quantità di prodotto configurabile non funziona come previsto.
feature: Shopping Cart, Products
role: Admin, Developer
exl-id: 8403b418-b197-4695-88a8-e322b18cd4ad
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-52736 [!UICONTROL Cart Price Rule] non funziona come previsto

La patch ACSD-52736 risolve il problema in cui [!UICONTROL Cart Price Rule] che include i requisiti per la quantità di prodotto configurabile non funziona come previsto. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.36. L’ID della patch è ACSD-52736. Il problema è stato risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

A [!UICONTROL Cart Price Rule] che include i requisiti per la quantità di prodotto configurabile non funziona come previsto.

<u>Passaggi da riprodurre</u>:

1. Crea una regola carrello:
   * [!UICONTROL Apply] = Percentuale di sconto sul prezzo del prodotto
   * [!UICONTROL Discount Amount] = 60
   * [!UICONTROL Maximum Qty Discount is Applied to] = 1
   * [!UICONTROL Discount Qty Step (Buy X)] = 1
   * Applica la regola solo agli articoli del carrello che soddisfano le seguenti condizioni: La quantità nel carrello è 1
2. Aggiungi un prodotto con [!UICONTROL Qty] = 2, al carrello.
3. Controlla i prezzi del carrello.

<u>Risultati previsti</u>:

La regola non viene applicata perché la quantità dei prodotti nel carrello è *2*.

<u>Risultati effettivi</u>:

Viene applicato lo sconto.

<u> Passaggi aggiuntivi necessari dopo l&#39;installazione della patch</u>:

Dopo l’applicazione della patch, le condizioni della regola del carrello vengono applicate utilizzando *Quantità* L&#39;attributo deve essere rimosso e aggiunto nuovamente.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
