---
title: "Patch MDVA-31168: il file di esportazione del prodotto non viene visualizzato in Admin"
description: La patch MDVA-31168 risolve il problema che causa la mancata visualizzazione del file CSV di esportazione del prodotto nell'elenco dei file CSV esportabili. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.10. Il problema è stato risolto nella versione 2.4.2 di Adobe Commerce.
exl-id: 780a926b-2aea-47c2-8f95-907cc779bfa4
feature: Admin Workspace, Categories, Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# Patch MDVA-31168: il file di esportazione del prodotto non viene visualizzato in Admin

La patch MDVA-31168 risolve il problema che causa la mancata visualizzazione del file CSV di esportazione del prodotto nell&#39;elenco dei file CSV esportabili. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.10. Il problema è stato risolto nella versione 2.4.2 di Adobe Commerce.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:** Adobe Commerce on-premise 2.3.5-p2

**Compatibile con le versioni di Adobe Commerce:** Adobe Commerce sull’infrastruttura cloud e Adobe Commerce on-premise 2.3.0 - 2.4.1.

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Prerequisiti</u>:

Installa Adobe Commerce con dati di esempio.

<u>Passaggi da riprodurre:</u>

1. Creare un prodotto scaricabile e assegnarlo a **Borse** categoria.
1. Avvia un&#39;esportazione per tutti i prodotti.
1. Esegui il comando seguente da CLI:    ```php    bin/magento queue:consumers:start exportProcessor --single-thread --max-messages=10000    ```

<u>Risultati previsti:</u>

Il file CSV di esportazione del prodotto con tutti i prodotti viene visualizzato nell’elenco dei file in Amministratore, come previsto.

<u>Risultati effettivi:</u>

Il file CSV di esportazione del prodotto con tutti i prodotti non viene visualizzato nell’elenco in Admin, anche se il file con solo le intestazioni viene generato in `/var` sul server.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
