---
title: "MDVA-22383: gli indicizzatori della regola di destinazione sono lenti nell'indicizzazione"
description: La patch MDVA-22383 risolve il problema relativo ai tempi eccessivamente lunghi necessari per la reindicizzazione degli indicizzatori Prodotto/Target e Regola di destinazione/Prodotto. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20. L'ID della patch è MDVA-22383. Il problema è stato risolto in Adobe Commerce 2.3.5.
exl-id: fbf28983-5883-4769-90bd-1c97c2b2e2b8
source-git-commit: 975f5b5c95ad488128a5dbb3488b8d54f7b73b59
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# MDVA-22383: gli indicizzatori della regola di destinazione sono lenti nell&#39;indicizzazione

La patch MDVA-22383 risolve il problema relativo ai tempi eccessivamente lunghi necessari per la reindicizzazione degli indicizzatori Prodotto/Target e Regola di destinazione/Prodotto. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20. L&#39;ID della patch è MDVA-22383. Il problema è stato risolto in Adobe Commerce 2.3.5.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:** Adobe Commerce sull’infrastruttura cloud 2.3.2

**Compatibile con le versioni di Adobe Commerce:** Adobe Commerce sull’infrastruttura cloud e Adobe Commerce on-premise 2.3.0-2.3.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La reindicizzazione degli indicizzatori Prodotto/Target e Regola di destinazione/Prodotto richiede troppo tempo.

<u>Prerequisiti:</u> il problema si verifica quando il numero di prodotti è elevato.

<u>Passaggi da riprodurre:</u>

1. Crea una regola target con prodotti che soddisfino le condizioni. Le condizioni devono aggiungere più prodotti alla raccolta e avere attributi (non categorie o attributi impostati).
1. Esegui il comando seguente:

   ```bash
       bin/magento indexer:reindex targetrule_product_rule
   ```

<u>Risultato effettivo:</u>

La reindicizzazione è bloccata; il salvataggio del prodotto è bloccato.

<u>Risultato previsto:</u>

Reindicizzazione completata.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sezione.
