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

La patch MDVA-31168 risolve il problema che causa la mancata visualizzazione del file CSV di esportazione del prodotto nell&#39;elenco dei file CSV esportabili. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.10. Il problema è stato risolto nella versione 2.4.2 di Adobe Commerce.

## Prodotti e versioni interessati

**La patch è stata creata per Adobe Commerce versione:** Adobe Commerce on-premise 2.3.5-p2.

**Compatibile con le versioni di Adobe Commerce:** Adobe Commerce su infrastruttura cloud e Adobe Commerce on-premise 2.3.0 - 2.4.1.

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Prerequisiti</u>:

Installa Adobe Commerce con dati di esempio.

<u>Passaggi da riprodurre:</u>

1. Crea un prodotto scaricabile e assegnalo alla categoria **Bagagli**.
1. Avvia un&#39;esportazione per tutti i prodotti.
1. Esegui il comando seguente da CLI:    ```php    bin/magento queue:consumers:start exportProcessor --single-thread --max-messages=10000    ```

<u>Risultati previsti:</u>

Il file CSV di esportazione del prodotto con tutti i prodotti viene visualizzato nell’elenco dei file in Amministratore, come previsto.

<u>Risultati effettivi:</u>

Il file CSV di esportazione del prodotto con tutti i prodotti non viene visualizzato nell&#39;elenco in Admin, anche se il file con solo intestazioni verrà generato nella cartella `/var` sul server.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
