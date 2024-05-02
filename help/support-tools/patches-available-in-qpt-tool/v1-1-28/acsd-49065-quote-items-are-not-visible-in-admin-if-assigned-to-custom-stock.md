---
title: "ACSD-49065: gli elementi del preventivo non sono visibili in admin"
description: Applica la patch ACSD-49065 per risolvere il problema Adobe Commerce, se gli elementi del preventivo non sono visibili nell’amministratore se sono assegnati solo al titolo personalizzato.
exl-id: 3a5ceb4c-4c94-4938-98d9-9171f2633056
feature: Admin Workspace, B2B, Orders, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-49065: gli elementi del preventivo non sono visibili in admin

La patch ACSD-49065 risolve il problema per cui gli elementi dell&#39;offerta non sono visibili nell&#39;amministratore se sono assegnati solo all&#39;azione personalizzata. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28. L’ID della patch è ACSD-49065. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli elementi del preventivo non sono visibili nell&#39;amministratore se sono assegnati solo al titolo personalizzato.

Prerequisiti:

**[!UICONTROL B2B]** e **[!UICONTROL Inventory]** I moduli devono essere installati.

<u>Passaggi da riprodurre</u>:

1. Abilita **[!UICONTROL Company]** e **[!UICONTROL B2B Quote]** in **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.
1. Creare un secondario **[!UICONTROL Inventory Source]** e assegnarlo a un secondario **[!UICONTROL Inventory Stock]**.
1. Crea un nuovo prodotto assegnando solo il secondario (non predefinito) **[!UICONTROL Inventory Source]**.
1. Vai alla vetrina e crea un nuovo account aziendale. Accedi come **[!UICONTROL Company Admin]** e aggiungi il prodotto creato al carrello.
1. Accedi al carrello e *[!UICONTROL Request a Quote]*.
1. Rivolgiti all’amministratore e visualizza il preventivo richiesto all’indirizzo **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**.

<u>Risultati previsti</u>:

Gli elementi sono visibili nel nuovo preventivo creato con i nuovi prodotti senza dover salvare nuovamente i prodotti.

<u>Risultati effettivi</u>:

Il *[!UICONTROL Items Quoted]* La sezione è vuota. Se salvi nuovamente il prodotto appena creato, gli elementi vengono visualizzati.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
