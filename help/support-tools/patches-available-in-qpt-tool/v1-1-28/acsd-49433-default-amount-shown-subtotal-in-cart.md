---
title: "ACSD-49433: importo predefinito visualizzato come subtotale nel carrello della gift card"
description: Applica la patch ACSD-49433 per risolvere il problema di Adobe Commerce, in cui l’importo predefinito viene visualizzato come subtotale nel carrello per la gift card con un importo aperto.
exl-id: e2a887bb-c15a-43a6-a145-b295deef399b
feature: Admin Workspace, Gift, Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-49433: importo predefinito visualizzato come subtotale nel carrello per gift card

La patch di ACSD-49433 risolve il problema per cui l&#39;importo predefinito viene visualizzato come subtotale nel carrello per la gift card con un importo aperto. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28. L’ID della patch è ACSD-49433. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;importo predefinito viene visualizzato come subtotale nel carrello della gift card con un importo aperto.

<u>Passaggi da riprodurre</u>:

1. Creare una gift card.
1. Assicurarsi che l&#39;importo aperto sia impostato su *[!UICONTROL Yes]* (tra $50 e $500).
1. Vai al prodotto [!UICONTROL Gift Card] nella vetrina e scegli un altro importo dal menu a discesa.
1. Specificare $100 nell&#39;importo in USD.
1. Compila gli altri campi e aggiungili al carrello.
1. Vai al mini-carrello o alla pagina del carrello.

<u>Risultati previsti</u>:

Il subtotale mostra la quantità immessa dall&#39;utente.

<u>Risultati effettivi</u>:

Il subtotale mostra l&#39;importo predefinito della gift card.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
