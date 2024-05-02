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

# ACSD-46683: Prezzi di spedizione *Non ancora calcolato*

La patch ACSD-46683 risolve il problema relativo al prezzo di spedizione *Non ancora calcolato*. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30. L’ID della patch è ACSD-46683. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il prezzo di spedizione è indicato *Non ancora calcolato*.

<u>Prerequisiti</u>:

I moduli Adobe Commerce Inventory management (MSI) sono installati.

<u>Passaggi da riprodurre</u>:

1. Creare un prodotto semplice e impostarne il prezzo su *$ 34*.
1. Configura il metodo di consegna spedizione gratuita.
1. Configura almeno un altro metodo di consegna.
1. Vai a **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]** e crea una nuova regola:
   * Nome = *75Altro*
   * Coupon = Nessuno
   * Priorità = 1
   * Condizioni: il subtotale è uguale o maggiore di *$ 75*
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
1. Nella fase di spedizione, seleziona **$0 - spedizione gratuita** e procedere alla fase di pagamento.
1. Controlla la [!UICONTROL Order Summary] nella fase di pagamento. Mostra *[!UICONTROL $0 - Free Shipping - Free]*.
1. Applica il codice coupon *35off*, aggiorna il subtotale e lo rende inferiore a 75 $.
1. Verifica [!UICONTROL Order Summary] nella fase di pagamento.

<u>Risultati previsti</u>:

Viene visualizzato il seguente messaggio: *Metodo di spedizione selezionato non disponibile. Seleziona un altro metodo di spedizione per questo ordine.*

<u>Risultati effettivi</u>:

Viene visualizzato il prezzo di spedizione *Non ancora calcolato*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
