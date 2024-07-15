---
title: "MDVA-38468: messaggio di errore durante il salvataggio della pagina CMS"
description: '"La patch di MDVA-38468 Adobe Commerce risolve il problema relativo al messaggio di errore: *Esiste già un elemento con lo stesso ID "PAGE_ID"* quando si salva una pagina CMS. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.26. L''ID della patch è MDVA-38468. Il problema è stato risolto in Adobe Commerce 2.3.6."'
exl-id: 7fe80308-50b7-4786-a43c-cce607eb606c
feature: CMS, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# MDVA-38468: messaggio di errore durante il salvataggio della pagina CMS

La patch di MDVA-38468 Adobe Commerce risolve il problema relativo al messaggio di errore: *Esiste già un elemento con lo stesso ID &quot;PAGE_ID&quot;* durante il salvataggio di una pagina CMS. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.26. L&#39;ID della patch è MDVA-38468. Il problema è stato risolto in Adobe Commerce 2.3.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**
Adobe Commerce sull’infrastruttura cloud 2.3.2-p2

**Compatibile con le versioni di Adobe Commerce:**
Adobe Commerce on-premise e Adobe Commerce sull’infrastruttura cloud 2.3.2-2.3.5-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando si tenta di salvare una pagina CMS, viene visualizzato il seguente messaggio di errore: *Esiste già un elemento con lo stesso ID &quot;PAGE_ID&quot;.*

<u>Passaggi da riprodurre</u>:

1. Crea un nuovo sito web + store + storeview.
1. Crea un altro sito Web + Store + Storeview.
1. Vai a **Contenuto** > **Gerarchia** > Aggiungi qualsiasi pagina CMS esistente alla struttura gerarchica.
1. Vai a **Contenuto** > **Pagine** > **Aggiungi nuova pagina**:
   * Aggiungi un titolo.
   * Nella sezione Pagina in siti Web, assegna a entrambe le visualizzazioni dello store create.
   * Nella sezione Gerarchia, assegna a qualsiasi categoria.
   * **Salva e continua modifica**.

<u>Risultati previsti</u>:

La pagina viene salvata senza errori.

<u>Risultati effettivi</u>:

La pagina è stata salvata, ma viene visualizzato il seguente messaggio di errore: *Esiste già un elemento (Magento\VersionsCms\Model\Hierarchy\Node) con lo stesso ID &quot;PAGE_ID&quot;.*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili nello strumento QPT, fare riferimento alla sezione [Patch disponibili nello strumento QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
