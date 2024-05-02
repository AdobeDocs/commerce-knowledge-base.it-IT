---
title: "ACSD-54418: l’importo dello sconto fisso aggiunto in modo errato al prodotto secondario del bundle a prezzo dinamico"
description: Applica la patch ACSD-54418 per risolvere il problema di Adobe Commerce in cui l’importo dello sconto fisso viene applicato in modo errato a ciascun prodotto secondario del bundle a prezzo dinamico.
feature: Shopping Cart
role: Admin, Developer
exl-id: f9a00a4b-0a57-4a61-8b7c-6385e0751991
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-54418: l’importo dello sconto fisso aggiunto in modo errato al prodotto secondario del bundle a prezzo dinamico.

La patch ACSD-54418 risolve il problema in cui l’importo dello sconto fisso viene applicato in modo errato a ciascun prodotto secondario del bundle a prezzo dinamico. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.42. L’ID della patch è ACSD-54418. Tieni presente che il problema è risolto in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’importo dello sconto fisso viene applicato in modo errato a ciascun prodotto secondario del bundle a prezzo dinamico.

<u>Passaggi da riprodurre</u>:

1. Creare un **[!UICONTROL bundle product]** con prezzi dinamici e *2* opzioni bundle.
1. Creare un **[!UICONTROL cart price rule]** con un codice coupon specifico che si applica solo al prodotto nel pacchetto **[!UICONTROL SKU]** e ha uno sconto fisso.
1. Aggiungi il prodotto nel carrello.
1. Applica **[!UICONTROL coupon code]**.
1. Controlla lo sconto applicato al carrello.

<u>Risultati previsti</u>:

Lo sconto viene applicato una sola volta all&#39;intero prodotto.

<u>Risultati effettivi</u>:

Lo sconto viene applicato a ogni prodotto secondario del bundle.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
