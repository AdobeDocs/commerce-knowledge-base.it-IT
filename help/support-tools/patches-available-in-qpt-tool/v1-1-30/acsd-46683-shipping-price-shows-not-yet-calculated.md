---
title: "ACSD-46683: prezzo di spedizione indicato *Non ancora calcolato*"
description: Applica la patch ACSD-46683 per risolvere il problema Adobe Commerce in cui il prezzo di spedizione è *Non ancora calcolato*.
exl-id: 77986612-87b7-4f50-afaf-1cfe9a4feb6f
feature: Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# ACSD-46683: il prezzo di spedizione mostra *Non ancora calcolato*

La patch di ACSD-46683 risolve il problema relativo al prezzo di spedizione che indica *Non ancora calcolato*. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30. L’ID della patch è ACSD-46683. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il prezzo di spedizione indica *Non ancora calcolato*.

<u>Prerequisiti</u>:

I moduli Adobe Commerce Inventory management (MSI) sono installati.

<u>Passaggi da riprodurre</u>:

1. Creare un prodotto semplice e impostarne il prezzo su *$34*.
1. Configura il metodo di consegna spedizione gratuita.
1. Configura almeno un altro metodo di consegna.
1. Vai a **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]** e crea una nuova regola:
   * Nome = *75more*
   * Coupon = Nessuno
   * Priorità = 1
   * Condizioni: Subtotale uguale o maggiore di *$75*
   * Azioni:
      * Applica a importo spedizione = Sì
      * Ignora regole successive = No
      * Spedizione gratuita = per spedizioni con articoli corrispondenti
1. Crea un&#39;altra regola di prezzo carrello:
   * Nome = *35off*
   * Priorità = 0
   * Coupon = Coupon specifico
   * Codice coupon = 35off
   * Azioni:
      * Applica = percentuale di sconto sul prezzo del prodotto
      * Importo sconto = 35
      * Applica a importo spedizione = No
      * Ignora regole successive = Sì
      * Spedizione gratuita = No
1. Apri la vetrina e aggiungi tre prodotti al carrello in modo che il subtotale superi $ 75.
1. Procedi al pagamento come ospite.
1. Nel passaggio di spedizione, selezionare **$0 - spedizione gratuita** e procedere al passaggio di pagamento.
1. Controlla [!UICONTROL Order Summary] nel passaggio di pagamento. Mostra *[!UICONTROL $0 - Free Shipping - Free]*.
1. Applicando il codice coupon *35off*, il subtotale verrà aggiornato e sarà inferiore a $75.
1. Controlla [!UICONTROL Order Summary] nel passaggio di pagamento.

<u>Risultati previsti</u>:

Viene visualizzato il seguente messaggio: *Il metodo di spedizione selezionato non è disponibile. Selezionare un altro metodo di spedizione per questo ordine.*

<u>Risultati effettivi</u>:

Nel prezzo di spedizione viene visualizzato *Non ancora calcolato*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
