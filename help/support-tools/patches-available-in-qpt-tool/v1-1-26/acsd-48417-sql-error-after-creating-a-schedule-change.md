---
title: 'ACSD-48417: errore SQL dopo la creazione di una modifica della pianificazione'
description: Applicare la patch ACSD-48417 per risolvere il problema di Adobe Commerce che causa un errore SQL dopo la creazione di una modifica della pianificazione per un prodotto e il salvataggio di un altro prodotto.
exl-id: 2bbf3bb5-dec8-43b3-81f1-be0dc53d1f46
feature: Storage
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# ACSD-48417: errore SQL dopo la creazione di una modifica della pianificazione

La patch ACSD-48417 risolve il problema relativo alla visualizzazione di un errore SQL dopo la creazione di una modifica della pianificazione per un prodotto e il salvataggio di un altro prodotto. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26. L’ID della patch è ACSD-48417. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Viene visualizzato un errore SQL dopo aver creato una modifica della pianificazione per un prodotto e aver salvato un altro prodotto.

<u>Passaggi da riprodurre</u>:

1. Installare Magento 2.4-sviluppare EE + dati di esempio.
1. Passa al pannello di amministrazione > **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Modificare qualsiasi prodotto (ad esempio, Duffle Bag Joust [SKU: 24-MB01]).
1. Pianifica un nuovo aggiornamento:
   * Seleziona **[!UICONTROL Save as a New Update]**
   * Nome aggiornamento: &quot;Update 1&quot;
   * Data inizio: ora corrente +1 min
   * Data di fine: ora corrente +1 ora
   * Modifica il nome del prodotto in: &quot;Joust Duffle Bag 2&quot;
   * Salva il prodotto.
1. Vai a CLI ed esegui cron e attendi che venga applicata la pianificazione.

   ```
   bin/magento cron:run && bin/magento cron:run
   ```

1. Di nuovo, vai a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** e modifica qualsiasi prodotto configurabile (ad esempio, Chaz Kangeroo Hoodie [SKU: MH01]).

   * Disattiva tutte le varianti. Passare alla colonna Azioni > **[!UICONTROL Select]** > **[!UICONTROL Disable Product]**.
   * Salva quello configurabile.

<u>Risultati previsti</u>:

Nessun errore durante il salvataggio del prodotto.

<u>Risultati effettivi</u>:

Si verifica il seguente errore:

```SQL
SQLSTATE[23000]: Integrity constraint violation: 1048 Column 'sku' cannot be null, query was: INSERT INTO `catalog_product_entity` (`entity_id`, `sku`, `row_id`, `created_in`, `updated_in`) VALUES (?, ?, ?, ?, ?)
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
