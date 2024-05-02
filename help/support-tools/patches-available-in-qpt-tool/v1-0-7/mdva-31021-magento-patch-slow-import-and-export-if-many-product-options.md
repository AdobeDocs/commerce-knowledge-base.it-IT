---
title: "MDVA-31021: importazione ed esportazione lente se molte opzioni di prodotto"
description: La patch MDVA-31021 risolve il problema quando l'importazione/esportazione richiede più tempo del previsto con un numero elevato di opzioni di prodotto. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7.
exl-id: d294b30d-b734-4bd6-bf1a-c116b789a63c
feature: Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# MDVA-31021: importazione ed esportazione lente se molte opzioni di prodotto

La patch MDVA-31021 risolve il problema quando l&#39;importazione/esportazione richiede più tempo del previsto con un numero elevato di opzioni di prodotto. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Se sono presenti almeno 100.000 record nel `catalog_product_option` , la convalida del file di funzione di importazione/esportazione richiede più tempo del previsto. Prima di importare/esportare, per verificare la convalida delle opzioni, Adobe Commerce carica le opzioni prodotto per tutti i prodotti esistenti.

<u>Prerequisiti</u>:

Adobe Commerce store con 5000 prodotti con opzioni personalizzate. Ogni prodotto deve avere almeno quattro opzioni personalizzate tra cui scegliere due o più opzioni in modo che vi siano 100.000 record in `catalog_product_option` tabella.

<u>Passaggi da riprodurre</u>:

1. Per un **Importa** esempio: crea un file di importazione CSV con uno degli SKU dall’amministratore di Commerce.
1. Aggiungi quattro opzioni personalizzate al file di importazione CSV.
1. Prova a importare il file CSV da Commerce Admin.

<u>Risultati previsti</u>:

La funzione di importazione o esportazione viene completata come previsto. La convalida richiede meno di 10 secondi per essere completata con un prodotto.

<u>Risultati effettivi</u>:

La funzione di importazione o esportazione richiede più tempo del previsto. La convalida richiede più di 10 secondi per essere completata con un solo prodotto.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
