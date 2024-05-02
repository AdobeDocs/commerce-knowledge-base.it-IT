---
title: "Patch MDVA-31224: la reindicizzazione del prezzo del prodotto richiede troppo tempo"
description: La patch MDVA-31224 risolve il problema quando il reindice dei prezzi dei prodotti richiede troppo tempo o non viene mai completato. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.7.
exl-id: 17f83fbf-9a43-4a65-b560-5f729b037c17
feature: Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# Patch MDVA-31224: la reindicizzazione dei prezzi dei prodotti richiede troppo tempo

La patch MDVA-31224 risolve il problema quando il reindice dei prezzi dei prodotti richiede troppo tempo o non viene mai completato. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.7.

## Prodotti e versioni interessati

* La patch è stata progettata per Adobe Commerce sull’infrastruttura cloud 2.3.3.
* La patch è compatibile anche con Adobe Commerce on-premise e Adobe Commerce on cloud infrastructure 2.3.3 - 2.3.4-p2.

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il completamento della reindicizzazione dei prezzi dei prodotti richiede troppo tempo o non viene mai completato.

<u>Passaggi da riprodurre:</u>

1. Crea 6000 prodotti in bundle con 15 opzioni.
1. Crea 1 prodotto in bundle con 30 opzioni.
1. Esegui reindicizzazione prezzi da CLI:     `bin/magento indexer:reindex catalog_product_price`

<u>Risultati previsti:</u>

Il completamento della reindicizzazione dei prezzi dei prodotti richiede 1,5 ore o più.

<u>Risultati effettivi:</u>

Il completamento della reindicizzazione dei prezzi dei prodotti richiede poco tempo (un minuto o due).

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
