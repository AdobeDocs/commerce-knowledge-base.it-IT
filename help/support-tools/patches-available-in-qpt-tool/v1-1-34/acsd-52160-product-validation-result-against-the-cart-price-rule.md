---
title: "ACSD-52160: risultato della convalida del prodotto in base alla regola del prezzo del carrello"
description: Applica la patch ACSD-52160 per risolvere il problema di Adobe Commerce per cui il risultato della convalida del prodotto rispetto alla regola del prezzo del carrello non viene valutato correttamente in base alla condizione della regola*[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*.
exl-id: a371c539-4440-4c84-baa4-774c32f66e41
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# ACSD-52160: il risultato della convalida del prodotto in base alla regola del prezzo del carrello non viene valutato correttamente

La patch ACSD-52160 risolve il problema per cui il risultato della convalida del prodotto rispetto alla regola del prezzo del carrello non viene valutato correttamente in base alla condizione della regola *[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.34. L’ID della patch è ACSD-52160. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il risultato della convalida del prodotto rispetto alla regola prezzo carrello non viene valutato correttamente in base alla condizione della regola *[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*.

<u>Passaggi da riprodurre</u>:

1. Crea due prodotti assegnati a due diverse categorie.
1. Creare un **[!UICONTROL Cart Price Rule]** con condizioni come:

   * **SKU 1** nel *[!UICONTROL FOUND]* parametro
   * **SKU 2** nel *[!UICONTROL NOT FOUND]* parametro

1. Aggiungi entrambi i prodotti al carrello.
1. Applica il codice del coupon.

<u>Risultati previsti</u>

Il codice coupon non viene applicato in quanto il carrello contiene prodotti della categoria con restrizioni.

<u>Risultati effettivi</u>

Il codice del coupon viene applicato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) nel [!DNL Quality Patches Tool] guida.
