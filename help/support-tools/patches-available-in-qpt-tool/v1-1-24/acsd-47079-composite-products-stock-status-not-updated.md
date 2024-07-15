---
title: "ACSD-47079: lo stato delle scorte dei prodotti compositi non viene aggiornato quando cambia lo stato delle scorte dei sottoprodotti"
description: Applicare la patch ACSD-47079 per risolvere il problema Adobe Commerce per cui lo stato delle scorte dei prodotti compositi (bundle, raggruppati e configurabili) non viene aggiornato quando lo stato delle scorte dei sottoprodotti cambia tramite REST API POST /rest/V1/inventory/source-items.
exl-id: 603e4548-fb04-43b4-a033-4f2c7f665fae
feature: Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-47079: lo stato delle scorte dei prodotti compositi non viene aggiornato quando cambia lo stato delle scorte dei sottoprodotti

La patch ACSD-47079 risolve il problema che impedisce l&#39;aggiornamento dello stato delle scorte dei prodotti compositi (bundle, raggruppati e configurabili) quando lo stato delle scorte dei sottoprodotti viene modificato tramite REST API POST `/rest/V1/inventory/source-items`. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24. L’ID della patch è ACSD-47079. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.4-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Lo stato del magazzino dei prodotti compositi (bundle, raggruppati e configurabili) non viene aggiornato quando lo stato del magazzino dei sottoprodotti viene modificato tramite REST API POST `/rest/V1/inventory/source-items`.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto configurabile, in bundle e raggruppato con un semplice prodotto secondario per ciascuno di essi.
1. Impostare ogni stato di prodotto figlio semplice su **[!UICONTROL Out of Stock]** utilizzando la chiamata API `source-items`.
1. Ora controlla lo stato delle scorte del prodotto principale.

<u>Risultati previsti</u>:

Lo stato del prodotto padre è [!UICONTROL Out of Stock].

<u>Risultati effettivi</u>:

Lo stato del prodotto padre è [!UICONTROL In Stock].

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
