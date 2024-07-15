---
title: "MDVA-35064: l'URL viene riscritto e non generato per i file configurabili creati tramite API"
description: La patch MDVA-35064 risolve il problema relativo alla mancata generazione di riscritture URL per "Tutte le visualizzazioni dello store" per i prodotti creati tramite API. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17. Il problema è stato risolto in Adobe Commerce 2.4.3.
exl-id: 0898c5b3-d361-4bcb-af3a-7f76ac8a23e1
feature: REST, Categories, Configuration
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# MDVA-35064: l&#39;URL viene riscritto e non generato per i file configurabili creati tramite API

La patch MDVA-35064 risolve il problema relativo alla mancata generazione di riscritture URL per &quot;Tutte le visualizzazioni dello store&quot; per i prodotti creati tramite API. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17. Il problema è stato risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.5-p1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce on-premise e Adobe Commerce sull’infrastruttura cloud 2.3.3-2.4.2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando i prodotti configurabili vengono creati tramite API, le riscritture URL non vengono generate.

<u>Passaggi da riprodurre</u>:

1. Crea un nuovo sito Web, store e visualizzazione store.
1. Crea una nuova categoria.
1. Crea un nuovo prodotto e assegnalo alla categoria appena creata.
1. Assegna il prodotto al sito Web principale e al nuovo sito Web.
1. Controlla la tabella URL e assicurati che contenga le voci per il prodotto, la categoria/prodotto per ogni negozio su ciascun sito web.
1. Rimuovi il prodotto per il secondo sito Web.

<u>Risultati previsti</u>:

La tabella URL contiene voci relative a prodotto, categoria/prodotto solo per i negozi del primo sito Web.

<u>Risultati effettivi</u>:

La tabella URL contiene riscritture URL per tutti gli archivi su tutti i siti Web.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
