---
title: "MDVA-36286: l’anteprima di Page Builder si interrompe se lo SKU si trova in categorie diverse"
description: La patch MDVA-36286 risolve il problema relativo all'interruzione dell'anteprima del widget Prodotti Page Builder se lo stesso SKU ha una posizione diversa nelle sottocategorie. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.23. Il problema è stato risolto in Adobe Commerce 2.4.3.
exl-id: 0f7d2506-569a-4b70-82bf-0f153014c48a
feature: CMS, Categories, Page Builder
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# MDVA-36286: l&#39;anteprima di Page Builder si interrompe se lo SKU si trova in categorie diverse

La patch MDVA-36286 risolve il problema relativo all&#39;interruzione dell&#39;anteprima del widget Prodotti Page Builder se lo stesso SKU ha una posizione diversa nelle sottocategorie. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.23. Il problema è stato risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.6

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.6 - 2.4.2-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Passaggi da riprodurre:</u>

1. Crea una categoria con alcuni prodotti.
   ![products_magento_ordered.png](/help/support-tools/patches-available-in-qpt-tool/assets/products_magento_ordered.png)
1. Crea una sottocategoria con gli stessi prodotti ma con posizioni diverse.
   ![products_magento_difference_position.png](/help/support-tools/patches-available-in-qpt-tool/assets/products_magento_different_position.png)
1. Modifica il contenuto di una pagina CMS per aggiungere un widget prodotto tramite Page Builder. (Seleziona la categoria principale precedente).
   ![cms_page_magento.png](/help/support-tools/patches-available-in-qpt-tool/assets/cms_page_magento.png)
1. Salva e attendi l’anteprima del contenuto.

<u>Risultati previsti:</u>

Nell’anteprima del contenuto viene visualizzato il widget del prodotto.

<u>Risultati effettivi:</u>

Viene visualizzato un errore:

*Si è verificato un errore durante la generazione del contenuto.*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
