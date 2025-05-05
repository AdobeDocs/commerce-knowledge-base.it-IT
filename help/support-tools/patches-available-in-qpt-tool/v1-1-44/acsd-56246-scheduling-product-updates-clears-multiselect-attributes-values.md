---
title: 'ACSD-56246: la pianificazione degli aggiornamenti dei prodotti cancella i valori degli attributi a selezione multipla'
description: Applica la patch ACSD-56246 per risolvere il problema di Adobe Commerce per cui la pianificazione degli aggiornamenti dei prodotti cancella i valori degli attributi a selezione multipla.
feature: Products, Attributes, Staging
role: Admin, Developer
exl-id: ddca8ac0-6aa8-4bf1-b8c2-4819758cb198
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-56246: la pianificazione degli aggiornamenti dei prodotti cancella i valori degli attributi a selezione multipla

La patch ACSD-56246 risolve il problema che comporta la cancellazione dei valori degli attributi a selezione multipla nella pianificazione degli aggiornamenti dei prodotti. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44. L’ID della patch è ACSD-56246. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il prodotto pianificato aggiorna e cancella i valori degli attributi a selezione multipla.

<u>Passaggi da riprodurre</u>:

1. Installa Adobe Commerce.
1. Vai a **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** e crea il seguente attributo:

   * Etichetta predefinita: Programma
   * Tipo di input del catalogo per il proprietario del negozio: Selezione multipla
   * Opzioni di gestione (valori dell&#39;attributo): Choice, Sunscape, Safetyshield
   * Codice attributo: customer_program
   * Ambito: globale
   * Opzioni Aggiungi a colonna: No
   * Usa in opzioni filtro: No
   * Proprietà vetrina
   * Posizione: *333*
   * Consenti tag HTML in Storefront: no

1. Esegui
   `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`.
1. Esegui
   `bin/magento setup:upgrade`.
1. Vai a **[!UICONTROL Admin]** > Scegli un prodotto semplice > Seleziona tutti gli elementi nell&#39;attributo del programma > Fai clic su **[!UICONTROL Save the product]**.
1. Pianifica un aggiornamento per questo prodotto nel minuto successivo ed esegui il comando seguente per far funzionare la gestione temporanea del contenuto:
   `for i in {1..100}; do bin/magento cron:run; done`.

<u>Risultati previsti</u>:

L&#39;attributo **[!UICONTROL program]** del prodotto non deve essere modificato.

<u>Risultati effettivi</u>:

L&#39;attributo **[!UICONTROL program]** del prodotto è cancellato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
