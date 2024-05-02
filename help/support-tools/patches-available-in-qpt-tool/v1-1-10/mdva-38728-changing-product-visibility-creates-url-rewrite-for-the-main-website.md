---
title: "MDVA-38728: la modifica della visibilità del prodotto crea la riscrittura dell’URL per il sito web principale"
description: La patch MDVA-38728 risolve il problema relativo alla modifica della visibilità del secondo sito Web in modo da creare un URL riscritto per il sito Web principale. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10. L'ID della patch è MDVA-38728. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: ad1d5f82-294d-485d-acd3-28c3cd0fbf56
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# MDVA-38728: la modifica della visibilità del prodotto crea la riscrittura dell&#39;URL per il sito Web principale

La patch MDVA-38728 risolve il problema relativo alla modifica della visibilità del secondo sito Web in modo da creare un URL riscritto per il sito Web principale. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10. L&#39;ID della patch è MDVA-38728. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.2 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Modificando la visibilità del prodotto del secondo sito Web, viene creata una riscrittura URL per il sito Web principale.

<u>Passaggi da riprodurre</u>:

1. Crea un ulteriore sito Web, store e storeview.
1. Crea un prodotto semplice.
1. Imposta la visibilità su **Non visibile singolarmente**.
1. Assegna il prodotto solo al secondo sito Web.
1. Compila tutti gli altri campi obbligatori.
1. Salva il prodotto.
1. Avvia code MySQL:

   ```mysql
   bin/magento queue:consumers:start product_action_attribute.update &
   bin/magento queue:consumers:start product_action_attribute.website.update &
   ```

1. Passa a Elenco prodotti.
1. Seleziona il prodotto creato e aggiorna l’attributo di visibilità utilizzando l’aggiornamento di massa a Catalogo e Ricerca.
1. Controlla la riscrittura dell’URL.

<u>Risultati previsti</u>:

La riscrittura viene creata per il secondo sito Web a cui è assegnato il prodotto.

<u>Risultati effettivi</u>:

La riscrittura viene creata per il sito Web principale.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
