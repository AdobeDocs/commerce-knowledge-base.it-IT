---
title: "ACSD-50345: problemi reCAPTCHA durante il pagamento"
description: Applica la patch ACSD-50345 per risolvere il problema Adobe Commerce in cui le convalide reCAPTCHA v2 e v3 non sono riuscite durante il posizionamento degli ordini e durante il pagamento.
exl-id: ac8c8130-0e4d-4610-9a55-afa779cce7a0
feature: Checkout, Orders
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# ACSD-50345: problemi di reCAPTCHA durante il pagamento

La patch ACSD-50345 risolve il problema relativo al mancato funzionamento delle convalide reCAPTCHA v2 e v3 durante l’inserimento degli ordini e il pagamento. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.31. L’ID della patch è ACSD-50345. Il problema è stato parzialmente risolto in Adobe Commerce 2.4.6 e la sua risoluzione completa è prevista in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.5-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

**Caso #1**

Google reCAPTCHA v2 non viene ricaricato dopo l’invio di un pagamento non riuscito.

<u>Passaggi da riprodurre</u>

1. Configura **[!UICONTROL Google reCAPTCHA v2]** (*Non sono un robot*).
1. Abilita **[!UICONTROL reCAPTCHA]** per l&#39;estrazione.
1. Provare a effettuare un ordine senza fare clic su **[!UICONTROL reCAPTCHA]**.
1. Quando l&#39;utente riceve il messaggio di errore per la convalida reCAPTCHA (*reCAPTCHA non riuscita, riprovare*), fare clic su **[!UICONTROL reCAPTCHA]** e quindi provare a effettuare un ordine.

<u>Risultati previsti</u>

L’ordine non verrà effettuato con un reCAPTCHA errato.

<u>Risultati effettivi</u>

Viene generato un errore - Convalida di *reCAPTCHA non riuscita. Riprovare* e *Nessun carrello con ID = 4*

**Caso #2**

Google reCAPTCHA v3 Invisible non funziona al momento del pagamento e non è possibile effettuare l&#39;ordine. L&#39;evento `PlaceOrder` non è attivato.

<u>Passaggi da riprodurre</u>

1. Configura **[!UICONTROL reCAPTCHA v3 Invisible]** da **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Security]**.
1. Abilita **[!UICONTROL reCAPTCHA v3 Invisible]** per il pagamento/inserimento di un ordine nella scheda **[!UICONTROL Storefront]**.
1. Provare a effettuare un ordine con il metodo di pagamento [!UICONTROL Check/Money order].

<u>Risultati previsti</u>

L&#39;ordine deve essere effettuato con **[!UICONTROL reCAPTCHA]** attivato.

<u>Risultati effettivi</u>

Dopo aver fatto clic sul pulsante **[!UICONTROL Place Order]**, il pulsante viene disattivato e non si verifica nulla di più.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
