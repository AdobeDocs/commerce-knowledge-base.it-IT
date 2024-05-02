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

La patch ACSD-47079 risolve il problema che impedisce l’aggiornamento dello stato delle scorte dei prodotti compositi (bundle, raggruppati e configurabili) quando lo stato delle scorte dei sottoprodotti viene modificato tramite REST API POST `/rest/V1/inventory/source-items`. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24. L’ID della patch è ACSD-47079. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.4-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Lo stato stock dei prodotti compositi (bundle, raggruppati e configurabili) non viene aggiornato quando lo stato stock del sottoprodotto viene modificato tramite REST API POST `/rest/V1/inventory/source-items`.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto configurabile, in bundle e raggruppato con un semplice prodotto secondario per ciascuno di essi.
1. Imposta ogni stato di prodotto figlio semplice su **[!UICONTROL Out of Stock]** utilizzando `source-items` Chiamata API.
1. Ora controlla lo stato delle scorte del prodotto principale.

<u>Risultati previsti</u>:

Lo stato del prodotto principale è [!UICONTROL Out of Stock].

<u>Risultati effettivi</u>:

Lo stato del prodotto principale è [!UICONTROL In Stock].

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
