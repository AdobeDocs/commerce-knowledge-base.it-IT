---
title: '"ACSD-54739: *[!UICONTROL Product Stock]* stato non applicato per *[!UICONTROL Related Product Rules]*'''
description: Applicare la patch ACSD-54739 per risolvere il problema Adobe Commerce in cui *[!UICONTROL Product Stock]* lo stato non è applicato per *[!UICONTROL Related Product Rules]*.
feature: Products
role: Admin, Developer
exl-id: 7bc106b1-2c97-46a1-8bb6-71b99511e480
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# ACSD-54739 *[!UICONTROL Product stock]* stato non applicato per *[!UICONTROL Related Product Rules]*

La patch ACSD-54739 risolve il problema in cui *[!UICONTROL Product stock]* stato non applicato per *[!UICONTROL Related Product Rules]*. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43. L’ID della patch è ACSD-54739. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

*[!UICONTROL Product stock]* stato non applicato per *[!UICONTROL Related Product Rules]*.

<u>Passaggi da riprodurre</u>:

1. Imposta il **[!UICONTROL Display Out of Stock Products]** configurazione a *Sì*.
1. Vai a **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** > **[!UICONTROL Search quantity attribute]** e imposta *Sì* per la condizione della regola promozionale.
1. Crea la regola prodotto correlata. Vai a **[!UICONTROL Product rule information]** > **[!UICONTROL Products to match]** > Aggiungi una condizione con quantità attributo (selezionare in magazzino/esaurito).
1. Controlla i prodotti nel front-end.

<u>Risultati previsti</u>:

Le corrispondenze in-stock/out-of-stock di *[!UICONTROL Related Product Rules]*.

<u>Risultati effettivi</u>:

Il prodotto in magazzino/esaurito non corrisponde al *[!UICONTROL Related Product Rules]*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
