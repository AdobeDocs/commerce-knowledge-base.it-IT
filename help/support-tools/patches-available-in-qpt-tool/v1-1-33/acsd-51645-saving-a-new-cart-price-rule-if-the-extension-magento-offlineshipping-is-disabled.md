---
title: "ACSD-51645: salvataggio di una nuova regola prezzo carrello se l’estensione Magento_OfflineShipping è disabilitata"
description: Applica la patch ACSD-51645 per risolvere il problema di Adobe Commerce in cui si verifica un errore durante il salvataggio di una nuova Regola prezzo carrello se l’estensione Magento_OfflineShipping è disabilitata.
exl-id: 301086bb-7aab-4e74-93e6-9080eebcb026
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# ACSD-51645: salvataggio di una nuova regola prezzo carrello se l’estensione Magento_OfflineShipping è disabilitata

La patch ACSD-51645 risolve il problema che si verifica quando si salva una nuova Regola prezzo carrello se l’estensione Magento_OfflineShipping è disabilitata. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33. L’ID della patch è ACSD-51645. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Se l&#39;estensione `Magento_OfflineShipping` è disabilitata, verrà visualizzato un errore durante il salvataggio di una nuova regola prezzo carrello.

<u>Passaggi da riprodurre</u>:

1. Disattiva il modulo `Magento_OfflineShipping`.
1. Accedi a **Amministratore**.
1. Vai a **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]**.
1. Crea un nuovo **[!UICONTROL Cart Price Rule]**.
1. Compila i campi obbligatori.
1. Salva **[!UICONTROL Cart Price Rule]**.

<u>Risultati previsti</u>:

La regola prezzo carrello è stata salvata correttamente.

<u>Risultati effettivi</u>:

Si verifica il seguente errore:
`report.ERROR: Warning: Undefined array key "simple_free_shipping" in app/code/Magento/SalesRule/Controller/Adminhtml/Promo/Quote/Save.php on line 67 [] []`

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) nella guida di [!DNL Quality Patches Tool].
