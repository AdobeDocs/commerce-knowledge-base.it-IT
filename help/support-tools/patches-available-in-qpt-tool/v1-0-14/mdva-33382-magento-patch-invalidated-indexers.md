---
title: "patch MDVA-33382: indicizzatori invalidati"
description: La patch MDVA-33382 risolve il problema quando gli indicizzatori vengono invalidati dopo l'aggiunta, la rimozione o il riordinamento di prodotti in una categoria. Gli indicizzatori invalidati sono "catalog_category_product" , "catalogsearch_fulltext" (e i loro dipendenti).
exl-id: b4ac10ee-0f9d-4d7a-be72-c4d90ebadb10
feature: Catalog Management, Categories, Price Indexer
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# Patch MDVA-33382: indicizzatori invalidati

La patch MDVA-33382 risolve il problema quando gli indicizzatori vengono invalidati dopo l&#39;aggiunta, la rimozione o il riordinamento di prodotti in una categoria. Gli indicizzatori invalidati sono `catalog_category_product` , `catalogsearch_fulltext` (e i relativi dipendenti).

Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.14. Il problema verrà risolto in Adobe Commerce versione 2.4.3.

## Prodotti e versioni interessati

**La patch è stata creata per Adobe Commerce versione:** Adobe Commerce su infrastruttura cloud 2.3.4-p2

**Compatibile con le versioni di Adobe Commerce:** Adobe Commerce su infrastruttura cloud e Adobe Commerce on-premise 2.3.0 - 2.4.1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Passaggi da riprodurre</u>:

1. Imposta tutte le modalità indicizzatore su **Aggiorna secondo pianificazione**.
1. Rimuovere un prodotto da una pagina di modifica della categoria.
1. Salva la categoria.
1. Verificare lo stato degli indici nel back-end o in CLI.

<u>Risultati previsti</u>:

I seguenti indici non vengono invalidati: `catalog_category_product` , `catalogsearch_fulltext` (e i relativi dipendenti), come previsto.

<u>Risultati effettivi</u>:

I seguenti indici sono invalidati: `catalog_category_product` , `catalogsearch_fulltext` (e i relativi dipendenti).

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta le [patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
