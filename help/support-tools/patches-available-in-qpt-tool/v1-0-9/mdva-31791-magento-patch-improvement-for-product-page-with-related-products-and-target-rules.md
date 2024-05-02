---
title: "Patch MDVA-31791: miglioramento della pagina prodotti con prodotti correlati e regole di destinazione"
description: La patch MDVA-31791 migliora le prestazioni delle pagine dei prodotti quando si utilizzano [Prodotti correlati](https://docs.magento.com/user-guide/catalog/settings-advanced-related-products.html) o [Regole prodotti correlati](https://docs.magento.com/user-guide/marketing/product-related-rules.html) (regole di destinazione). Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9. Il problema è stato risolto in Adobe Commerce 2.4.1.
exl-id: e737bccb-d9eb-4794-9d6b-2c22fa8edaa2
feature: Marketing Tools, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# Patch MDVA-31791: miglioramento della pagina prodotti con prodotti correlati e regole di destinazione

La patch MDVA-31791 migliora le prestazioni delle pagine di prodotti quando [Prodotti correlati](https://docs.magento.com/user-guide/catalog/settings-advanced-related-products.html) o [Regole dei prodotti correlati](https://docs.magento.com/user-guide/marketing/product-related-rules.html) (regole di destinazione). Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9. Il problema è stato risolto in Adobe Commerce 2.4.1.

## Prodotti e versioni interessati

**La patch è stata creata per la versione Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.4.0

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce su infrastruttura cloud e Adobe Commerce on-premise 2.3.4, 2.3.4-p1, 2.3.4-p2, 2.4.0, 2.4.0-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Prestazioni ridotte delle pagine dei prodotti se si utilizzano prodotti correlati o regole di Target.

Prendere in considerazione l&#39;applicazione della patch MDVA-31791 se si desidera utilizzare [Prodotto correlato](https://docs.magento.com/user-guide/catalog/settings-advanced-related-products.html) o [Regole prodotto correlate](https://docs.magento.com/user-guide/marketing/product-related-rules.html) funzionalità.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
