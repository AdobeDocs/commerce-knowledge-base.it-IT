---
title: "MCP-87 Adobe Commerce patch: vetrina rotta"
description: La patch Adobe Commerce MCP-87 ha risolto il problema che rallenta la reindicizzazione delle scorte dei cataloghi. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13.
exl-id: 048b2764-6bbf-4a02-9a0a-dbea4e48f92a
feature: Storefront
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# Patch MCP-87 Adobe Commerce: vetrina rotta

La patch Adobe Commerce MCP-87 ha risolto il problema che rallenta la reindicizzazione delle scorte dei cataloghi. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce sull’infrastruttura cloud 2.4.0.

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.1 - 2.4.1.

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La reindicizzazione azionaria dei cataloghi con profili di grandi dimensioni è molto lenta.

<u>Passaggi da riprodurre:</u>

1. Accedi al pannello di amministrazione.
1. Accedi a: **Prodotti** > **Catalogo**.
1. Selezionare tutti gli elementi nella griglia Prodotti.
1. Seleziona **Aggiorna attributi** nell’elenco a discesa Seleziona azioni prodotto. Clic **Invia**.
1. Fai clic su **Inventario avanzato** dalla scheda Impostazioni avanzate. Cambia **Disponibilità scorte** a *In magazzino*. Clic **Salva**.
1. Esegui la reindicizzazione completa manualmente, esegui il seguente comando dalla radice: `bin/magento indexer:reindex`

<u>Risultato previsto:</u>

L’indicizzatore azionario reindicizza rapidamente.

<u>Risultato effettivo:</u>

L’indicizzatore azionario è molto lento e/o non completa.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
