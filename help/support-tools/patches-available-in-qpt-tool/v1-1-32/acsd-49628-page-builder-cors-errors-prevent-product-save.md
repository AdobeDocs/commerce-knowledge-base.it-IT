---
title: '"ACSD-49628: [!DNL Page Builder] Errori CORS impediscono il salvataggio del prodotto'''
description: Applicare la patch ACSD-49628 per risolvere il problema Adobe Commerce in cui [!DNL Page Builder] Gli errori CORS impediscono il salvataggio del prodotto.
exl-id: c6e2f0b3-aea0-4caf-8b69-9644b38c909c
feature: Categories, Page Builder, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-49628 [!DNL Page Builder] Errori CORS impediscono il salvataggio del prodotto

La patch ACSD-49628 risolve il problema dove [!DNL Page Builder] Gli errori CORS impediscono a un amministratore di salvare un prodotto. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.32. L’ID della patch è ACSD-49628. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

[!DNL Page Builder] Gli errori CORS impediscono il salvataggio di un prodotto.

<u>Passaggi da riprodurre</u>:

1. Accedi come amministratore.
1. Crea un ruolo utente con le seguenti autorizzazioni:

   * **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Products]**.
   * **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Categories]**.

1. Non aggiungere *[!UICONTROL Content]* autorizzazioni.
1. Crea un altro utente amministratore e assegna a questo utente i ruoli creati in precedenza.
1. Crea un prodotto e disconnettiti.
1. Accedi come secondo amministratore.
1. Prova a modificare e salvare il prodotto.

<u>Risultati previsti</u>:

Il secondo amministratore è in grado di salvare il prodotto, ma **[!UICONTROL Edit with Page Builder]** non viene visualizzato all’amministratore senza alcun *[!UICONTROL Content]* autorizzazioni.

<u>Risultati effettivi</u>:

Il secondo amministratore non è in grado di salvare il prodotto a causa di più [!DNL Page Builder] errori.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
