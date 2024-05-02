---
title: '"ACSD-53636: il prezzo normale non viene visualizzato su [!UICONTROL Product Listing] page'''
description: Applica la patch ACSD-53636 per risolvere il problema di Adobe Commerce, in cui il prezzo normale non viene visualizzato su *[!UICONTROL Product Listing]* pagine per prodotti configurabili che hanno prodotti secondari con prezzi speciali.
feature: Catalog Management, Products
role: Admin, Developer
exl-id: 97b4eb64-92d1-4db1-8e5b-915b16115663
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# ACSD-53636: il prezzo normale non viene visualizzato su *[!UICONTROL Product Listing]* pagina

La patch ACSD-53636 risolve il problema che non consente la visualizzazione del prezzo normale su *[!UICONTROL Product Listing]* pagine per prodotti configurabili con prodotti secondari a prezzi speciali. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43. L’ID della patch è ACSD-53636. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.4-p6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il prezzo normale non viene visualizzato su *[!UICONTROL Product Listing]* pagine per prodotti configurabili con prodotti secondari a prezzi speciali.

<u>Passaggi da riprodurre</u>:

1. Accedi all’amministratore e vai su **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** e creare o aprire qualsiasi prodotto configurabile.
2. Apri il prodotto secondario e aggiungi un prezzo speciale a tutti o a uno dei prodotti secondari e salva il prodotto.
3. Vai a front-end e apri la **[!UICONTROL Product Detail]** pagina del prodotto configurabile; sui campioni del prodotto secondario con prezzo speciale, vedrai *[!UICONTROL Regular price]* barrato (previsto).
4. Vai a front-end e apri la **[!UICONTROL Product Listing]** pagina del prodotto configurabile con prezzo speciale; osserva che le modifiche al campione di prodotto configurabile non visualizzano il prezzo regolare a differenza del *[!UICONTROL Product Detail Page]* e altri prodotti semplici.

<u>Risultati previsti</u>:

Il giorno *[!UICONTROL Product Listing]* pagina, il prodotto configurabile mostra il prezzo regolare per il suo prodotto secondario.

<u>Risultati effettivi</u>:

Il giorno *[!UICONTROL Product Listing]* pagina, il prodotto configurabile non mostra il prezzo regolare per il suo prodotto secondario.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
