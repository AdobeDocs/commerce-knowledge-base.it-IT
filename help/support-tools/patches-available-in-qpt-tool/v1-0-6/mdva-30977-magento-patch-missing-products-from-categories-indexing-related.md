---
title: "MDVA-30977: prodotti mancanti dalle categorie, indicizzazione correlata"
description: La patch MDVA-30977 risolve i problemi relativi ai prodotti visualizzati nelle pagine delle categorie della vetrina durante la reindicizzazione o azioni di massa con un numero elevato di prodotti. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6. I problemi sono pianificati per essere risolti in Adobe Commerce 2.4.2.
exl-id: 66ec4f53-c01d-4f87-a175-84f44a26f5d3
feature: Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# MDVA-30977: prodotti mancanti dalle categorie, indicizzazione correlata

La patch MDVA-30977 risolve i problemi relativi ai prodotti visualizzati nelle pagine delle categorie della vetrina durante la reindicizzazione o azioni di massa con un numero elevato di prodotti. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6. I problemi sono pianificati per essere risolti in Adobe Commerce 2.4.2.

## Prodotti e versioni interessati

La patch è stata creata per Adobe Commerce sull’infrastruttura cloud 2.3.4. È compatibile anche con Adobe Commerce on-premise 2.3.4.

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problemi

### Numero 1

Il numero di prodotti visualizzati nella pagina delle categorie della vetrina è diverso dopo ogni ricaricamento della pagina durante l&#39;aggiornamento di massa del prodotto.

<u>Passaggi da riprodurre:</u>

1. Crea almeno 30000 prodotti in due categorie: almeno 15000 prodotti in ciascuna categoria.
1. Vai a **Catalogo** > **Prodotti** in Commerce Admin.
1. Selezionare tutti i prodotti dalla griglia ed eseguire un aggiornamento dell&#39;attributo di massa. Ad esempio, imposta **Nuovo** = *Sì* attributo.
1. Esegui il processo cron di Magento utilizzando `bin/magento cron:run` due volte.
1. Aggiorna le pagine delle categorie in Storefront mentre Adobe Commerce esegue l&#39;aggiornamento dei 30000.

<u>Risultato previsto:</u>

Il numero di prodotti nelle categorie viene sempre 15000 all’aggiornamento di ogni pagina categoria.

<u>Risultato effettivo:</u>

Il numero di prodotti nelle categorie è diverso in ogni aggiornamento della pagina categoria.

### Numero 2

Quando si esegue la reindicizzazione completa dell’inventario, le pagine delle categorie diventano vuote e il valore *Impossibile trovare prodotti corrispondenti alla selezione* viene visualizzato il messaggio.

<u>Passaggi da riprodurre:</u>

1. Configura Adobe Commerce con Elasticsearch.
1. Aggiungi un nuovo sito web.
1. Crea una nuova origine e assegnala al nuovo sito Web utilizzando Gestisci scorte.
1. Creare prodotti 30000.
1. Assegna tutti i prodotti al nuovo sito Web e aggiungi l&#39;inventario alla nuova origine inventario.
1. Esegui una reindicizzazione completa.
1. Eseguire la reindicizzazione dell&#39;inventario eseguendo `bin/magento indexer:reindex inventory`
1. Sfoglia una categoria con un numero elevato di prodotti.

<u>Risultato previsto:</u>

Le pagine delle categorie visualizzano i prodotti come di consueto durante la reindicizzazione.

<u>Risultato effettivo:</u>

Le pagine delle categorie diventano vuote durante la reindicizzazione.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sezione.
