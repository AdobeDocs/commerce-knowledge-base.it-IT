---
title: "ACSD-45168: URL descrittivi SEO non generati per prodotti con attributi url_key sostituiti"
description: Applica la patch ACSD-45168 per risolvere il problema di Adobe Commerce, in cui gli URL compatibili con SEO non vengono generati per i prodotti con attributi url_key sostituiti a livello di visualizzazione dello store.
exl-id: cdba42ac-3c96-439b-befa-f0a13587b5d9
feature: Attributes, Cache, Categories, Marketing Tools, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-45168: URL descrittivi SEO non generati per prodotti con attributi url_key sostituiti

La patch ACSD-45168 risolve il problema della mancata generazione di URL compatibili con SEO per i prodotti con attributi url_key sostituiti a livello di visualizzazione store. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24. L’ID della patch è ACSD-45168. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli URL compatibili con SEO non vengono generati per i prodotti con attributi url_key sostituiti a livello di visualizzazione store.

<u>Passaggi da riprodurre</u>:

1. Imposta la configurazione come segue andando su **[!UICONTROL Commerce Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]**:
   * [!UICONTROL Use Categories Path for Product URLs] = *Sì*
   * [!UICONTROL Generate "category/product" URL Rewrites] = *Sì*
1. Pulisci la cache di configurazione.
1. Crea due categorie: [!UICONTROL Category 1] e [!UICONTROL Category 2].
1. Crea due prodotti: [!UICONTROL Product 1] in [!UICONTROL Category 1], [!UICONTROL Product 2] in [!UICONTROL Category 1].
1. Modifica l’ambito in [!UICONTROL Default Store View] per [!UICONTROL Product 1].
1. Deseleziona l’URL facoltativo [!UICONTROL Key] in [!UICONTROL Search Engine Optimization].
1. Salva il prodotto.
1. Torna a [!UICONTROL All Store Views].
1. Aggiungi [!UICONTROL Product 1] a [!UICONTROL Category 2], e aggiungi [!UICONTROL Product 2] a [!UICONTROL Category 2].
1. Controlla la [!UICONTROL url_rewrite] tabella o [!UICONTROL Marketing] > [!UICONTROL SEO & Search] > [!UICONTROL URL Rewrites].

<u>Risultati previsti</u>:

L’URL SEO-friendly per [!UICONTROL Category 2] è stato creato per [!UICONTROL Product 1].

<u>Risultati effettivi</u>:

L’URL SEO-friendly per [!UICONTROL Category 2] è mancante per [!UICONTROL Product 1] perché l’attributo chiave URL veniva sovrascritto per l’ambito di visualizzazione archivio.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
