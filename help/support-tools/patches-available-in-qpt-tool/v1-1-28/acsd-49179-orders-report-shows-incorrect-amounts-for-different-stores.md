---
title: "ACSD-49179: il rapporto Ordini mostra importi non corretti per negozi diversi."
description: Applica la patch ACSD-49179 per risolvere il problema Adobe Commerce, in cui il rapporto Ordini mostra importi non corretti in caso di valute diverse per negozi diversi.
exl-id: 01e4cd2d-6c33-4cf5-bf31-bbc34eaaed1a
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# ACSD-49179: il rapporto Ordini mostra importi non corretti per negozi diversi

La patch di ACSD-49179 risolve il problema relativo alla visualizzazione di importi non corretti nel rapporto Ordini in caso di valute diverse per negozi diversi. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28. L’ID della patch è ACSD-49179. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il rapporto Ordini mostra gli importi errati in caso di valute diverse per negozi diversi.

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Price]** e imposta [!UICONTROL Catalog Price Scope] = [!UICONTROL Website].
1. Crea una visualizzazione aggiuntiva per sito Web, store e store.
1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL General]** > **[!UICONTROL Currency Setup]** > **[!UICONTROL Currency Options]** e imposta:
   * Configurazione predefinita:
      * Valuta di base: USD
      * Valuta di visualizzazione predefinita: USD
      * Valute consentite: EUR, USD e THB (Baht thailandese)
   * Sito Web principale:
      * Valuta di base: EUR
      * Valuta di visualizzazione predefinita: EUR
      * Valute consentite: EUR
   * Nuovo sito Web aggiuntivo:
      * Valuta di base: THB (Baht tailandese)
      * Valuta di visualizzazione predefinita: THB (Thai Baht)
      * Valute consentite: THB (Baht thailandese)
1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Currency]** > **[!UICONTROL Currency Rates]** e imposta i tassi di conversione vuoti per THB (imposta i tassi su 1,0000).
1. Crea un prodotto, assegnalo a entrambi i siti web e ordina il prodotto nel sito web aggiuntivo creato in precedenza.
1. Assicurati che l’ordine sia in *Elaborazione* stato (fatturarlo).
1. Nel backend, vai a **[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Fai clic sul pulsante **[!UICONTROL Yellow]** avviso per aggiornare le statistiche.
1. Imposta l’ambito del rapporto sul sito web aggiuntivo creato in precedenza e imposta il filtro come segue:
   * [!UICONTROL Date Used]: [!UICONTROL Created]
   * [!UICONTROL Period]: [!UICONTROL Day]
   * [!UICONTROL From and To]: lo stesso giorno in cui è stato effettuato l’ordine dei test
   * [!UICONTROL Order Status]: [!UICONTROL Any]
   * [!UICONTROL Empty rows]: [!UICONTROL No]
   * [!UICONTROL Show Actual Values]: [!UICONTROL No]

<u>Risultati previsti</u>:

Totale vendite mostra l&#39;importo corretto convertito nella valuta del sito Web.

<u>Risultati effettivi</u>:

Il totale è zero.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
