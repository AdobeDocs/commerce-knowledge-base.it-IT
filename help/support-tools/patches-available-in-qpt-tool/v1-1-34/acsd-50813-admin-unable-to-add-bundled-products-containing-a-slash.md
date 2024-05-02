---
title: "ACSD-50813: l’amministratore non è in grado di aggiungere prodotti in bundle contenenti una barra"
description: Applica la patch ACSD-50813 per risolvere il problema di prestazioni di Adobe Commerce, in cui l’amministratore non può aggiungere prodotti in bundle contenenti una barra (`/`) nello SKU con la funzionalità *Add Products by SKU* (Aggiungi prodotti per SKU) all’ordine di amministrazione.
exl-id: 80dfe877-9dfd-44a9-9bf0-37e929642fc0
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-50813: l’amministratore non è in grado di aggiungere prodotti in bundle contenenti una barra

La patch ACSD-50813 risolve il problema per cui l’amministratore non può aggiungere prodotti in bundle contenenti una barra (`/`) nella SKU con *[!UICONTROL Add Products by SKU]* all&#39;ordine di amministrazione. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.34. L’ID della patch è ACSD-50813. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’amministratore non può aggiungere prodotti in bundle contenenti una barra (`/`) nella SKU con *[!UICONTROL Add Products by SKU]* all&#39;ordine di amministrazione.

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Crea un prodotto semplice.
1. Crea un nuovo prodotto incluso.
1. Aggiungi una barra (`/`) al centro dello SKU (Esempio: *Bu/ndle*).
1. Aggiungi un’opzione in bundle con **[!UICONTROL Input Type]** = *[!UICONTROL Dropdown]*.
1. Assegna all’opzione almeno un prodotto semplice.
1. Vai a **[!UICONTROL Sales]** > **[!UICONTROL Orders]** e creare un nuovo ordine.
1. Fai clic su **[!UICONTROL Add Products by SKU]**.
1. Inserisci il tuo SKU e fai clic su **[!UICONTROL Add to Order]**.
1. Apri la console del browser.
1. Fai clic su **[!UICONTROL Configure]**.

<u>Risultati previsti</u>:

Nessun errore.

<u>Risultati effettivi</u>:

Errore JS nella console:

*Errore non rilevato: errore di sintassi, espressione non riconosciuta: div[id=sku_bu/ndle]*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
