---
title: "ACSD-52399: prodotto con qtà vendibile 0 mostra in magazzino"
description: Applicare la patch ACSD-52399 per risolvere il problema di Adobe Commerce, in cui l'opzione del prodotto configurabile con qtà vendibile pari a 0 mostra *In magazzino* sulla pagina del prodotto.
feature: Products, Configuration
role: Admin, Developer
exl-id: 3c9e6edd-f7ce-492e-b74f-68354d8e2633
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-52399: Prodotto con qtà vendibile 0 mostra in magazzino

La patch di ACSD-52399 risolve il problema relativo alla visualizzazione di *In magazzino* nella pagina del prodotto da parte dell&#39;opzione del prodotto configurabile con una quantità di vendita pari a zero (0). Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.35. L’ID della patch è ACSD-52399. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.5-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;opzione di prodotto configurabile con una quantità di vendita pari a zero (0) mostra *In magazzino* nella pagina del prodotto.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto configurabile con l’opzione di prodotto quantità vendibile pari a zero (0).
1. Vai alla pagina del prodotto nella vetrina e seleziona il prodotto configurabile per controllare una variante/configurazione.
1. Selezionare **[!UICONTROL Add to Cart]**.

<u>Risultati previsti</u>:

Il pulsante *[!UICONTROL Add to Cart]* non è disponibile quando si seleziona *Configurazione prodotto esaurito*.

<u>Risultati effettivi</u>:

Nella vetrina sono disponibili varianti configurabili che puoi selezionare e aggiungere al carrello.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
