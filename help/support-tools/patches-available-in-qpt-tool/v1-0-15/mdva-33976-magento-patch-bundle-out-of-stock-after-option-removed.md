---
title: "Patch MDVA-33976: bundle esaurito dopo la rimozione dell'opzione"
description: La patch MDVA-33976 risolve il problema relativo alla visualizzazione di un prodotto bundle come esaurito dopo la rimozione di una delle opzioni in Admin. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT) 1.0.15](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp). Il problema è pianificato per essere risolto in Adobe Commerce 2.4.3.
exl-id: 2e2bc05b-ad31-4e87-b33e-3526f6a42478
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# Patch MDVA-33976: bundle esaurito dopo la rimozione dell&#39;opzione

La patch MDVA-33976 risolve il problema relativo alla visualizzazione di un prodotto bundle come esaurito dopo la rimozione di una delle opzioni in Admin. Questa patch è disponibile quando [Strumento Patch di qualità (QPT) 1.0.15](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) è installato. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:** Adobe Commerce sull’infrastruttura cloud 2.3.3

**Compatibile con le versioni di Adobe Commerce:** Adobe Commerce sull’infrastruttura cloud e Adobe Commerce on-premise 2.3.0-2.3.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Passaggi da riprodurre</u>:

1. Apri un prodotto bundle in Commerce Admin.
1. Rimuovi una delle opzioni del prodotto del bundle.
1. Salva le modifiche.
1. Apri il prodotto nella vetrina.

<u>Risultato previsto</u>:

Lo stato delle scorte del prodotto del bundle viene aggiornato in base allo stato delle scorte del prodotto figlio.

<u>Risultato effettivo</u>:

Il prodotto del bundle viene visualizzato come esaurito, indipendentemente dallo stato del prodotto secondario.

## Applicare la patch

Per applicare singole patch, utilizzare i seguenti collegamenti, a seconda del prodotto Adobe Commerce:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili nello strumento QPT, consultare [Patch disponibili nello strumento QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sezione.
