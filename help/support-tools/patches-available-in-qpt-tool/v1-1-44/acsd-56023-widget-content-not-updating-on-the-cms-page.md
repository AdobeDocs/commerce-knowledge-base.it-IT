---
title: "ACSD-56023: il contenuto del widget non viene aggiornato nella pagina CMS"
description: Applica la patch ACSD-56023 per risolvere il problema di Adobe Commerce, in cui il contenuto del widget non viene aggiornato nella pagina CMS
feature: CMS
role: Admin, Developer
exl-id: 2ff33b1c-ae92-4c59-83d2-e252bf543bab
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-56023: il contenuto del widget non viene aggiornato nella pagina CMS

La patch ACSD-56023 risolve il problema se il contenuto del widget non viene aggiornato nella pagina CMS. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44. L’ID della patch è ACSD-56023. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il contenuto del widget non viene aggiornato nella pagina CMS.

<u>Passaggi da riprodurre</u>:

1. Crea alcuni prodotti.
1. Crea la nuova pagina CMS e aggiungi nuovi widget di prodotti al contenuto:

   ```
      {{widget type="Magento\Catalog\Block\Product\Widget\NewWidget" display_type="new_products" show_pager="1" products_per_page="5" products_count="10" template="product/widget/new/content/new_grid.phtml" page_var_name="pnetpm"}} 
   ```

1. Apri la pagina creata nella vetrina. Assicurati di memorizzarlo nella cache.
1. Dall’amministratore, apri **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Scegli un prodotto per la modifica e lo switch **[!UICONTROL Set Product as New]** a *Sì*.
1. Vai alla pagina creata *Pagina CMS* di nuovo sul vetrina.

<u>Risultati previsti</u>:

La pagina contiene *Nuovo widget Prodotti* con i prodotti.

<u>Risultati effettivi</u>:

La pagina non contiene *Nuovo widget Prodotti* e i nuovi prodotti non vengono visualizzati.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
