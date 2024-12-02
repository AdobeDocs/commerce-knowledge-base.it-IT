---
title: 'ACSD-52133: impossibile salvare l’account del cliente dopo un aggiornamento'
description: Applica la patch ACSD-52133 per risolvere il problema di Adobe Commerce, a causa del quale non è possibile salvare un account cliente dopo un aggiornamento.
feature: Customers, Upgrade
role: Admin
exl-id: 0db7c79e-10e1-4850-81b5-4812fb051941
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-52133: impossibile salvare l’account del cliente dopo un aggiornamento

La patch ACSD-52133 risolve il problema che impediva il salvataggio di un account cliente dopo un aggiornamento. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.35. L’ID della patch è ACSD-52133. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;account cliente non può essere salvato dopo un aggiornamento.

<u>Passaggi da riprodurre</u>:

1. Installare Adobe Commerce versione 2.4.4.
1. Crea un cliente.
1. Aggiornare Adobe Commerce alla versione 2.4.6 dalla versione precedente della versione 2.4.4, in cui era già stato creato un cliente.
1. Impostare la chiave di crittografia come indicato di seguito in `env.php`:

   `d337b914e91ff703b1e94ba4156aadf0`

1. Impostare i valori seguenti nel database per qualsiasi cliente nella tabella `customer_entity`:

   ```
   -> rp_token as incr4869
   -> rp_token_created_at as "2021-04-29 20:06:14"
   ```

1. Vai a **[!UICONTROL Admin]** > **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.
1. Modifica il cliente per il quale sono stati aggiornati i valori precedenti.
1. Fai clic su **[!UICONTROL Save Customer]** o **[!UICONTROL Save and Continue Edit]**

<u>Risultati previsti</u>:

Il cliente viene salvato senza errori.

<u>Risultati effettivi</u>:

* Record cliente non salvato.
* L&#39;amministratore visualizza il seguente messaggio di errore: *Si è verificato un errore durante il salvataggio del cliente.*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
