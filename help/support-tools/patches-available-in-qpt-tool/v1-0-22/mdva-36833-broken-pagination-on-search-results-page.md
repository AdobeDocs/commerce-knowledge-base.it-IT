---
title: "MDVA-36833: paginazione interrotta nella pagina dei risultati della ricerca"
description: La patch MDVA-36833 risolve il problema relativo all'interruzione dell'impaginazione quando il catalogo condiviso è abilitato e alcuni prodotti sono stati esclusi dal catalogo condiviso. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22. L'ID della patch è MDVA-36833. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.3.
exl-id: 7105c4ed-48d9-4d4c-bf12-5914bbad62da
feature: Catalog Management, Search
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# MDVA-36833: paginazione interrotta nella pagina dei risultati della ricerca

La patch MDVA-36833 risolve il problema relativo all&#39;interruzione dell&#39;impaginazione quando il catalogo condiviso è abilitato e alcuni prodotti sono stati esclusi dal catalogo condiviso. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22. L&#39;ID della patch è MDVA-36833. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch è stata creata per Adobe Commerce versione:** Adobe Commerce (tutti i metodi di distribuzione) 2.4.2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’esclusione di alcuni prodotti dal catalogo condiviso causa il mancato raggiungimento dell’impaginazione per i risultati della ricerca.

<u>Passaggi da riprodurre:</u>

1. Abilita catalogo condiviso.
1. Vai a **Catalogo** > **Cataloghi condivisi** e configura il catalogo condiviso predefinito assegnandogli tutti i prodotti.
1. Carica la vetrina e cerca la giacca.
1. Prendi nota dei prodotti elencati nella prima pagina. Ci dovrebbero essere 12 prodotti.
1. Osserva 11 SKU dalla prima pagina. Vai al backend e carica il catalogo condiviso predefinito.
1. Annulla l’assegnazione degli SKU annotati in precedenza dal catalogo condiviso predefinito.
1. Vai alla vetrina e cerca &quot;giacca&quot;.
1. Controlla la prima pagina dei risultati della ricerca.

<u>Risultato effettivo:</u>

La prima pagina contiene un prodotto e gli altri prodotti sono disponibili nella seconda pagina.

<u>Risultato previsto:</u>

La prima pagina deve contenere 12 prodotti.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.


## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
