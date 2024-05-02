---
title: "MC-42528: la query GraphQL di categoryList mostra tutte le categorie"
description: La patch MC-42528 risolve il problema per cui la query GraphQL di "categoryList" restituisce sia le categorie assegnate che quelle non assegnate quando la categoria di navigazione di una particolare categoria è impostata su "Deny". Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4. L’ID della patch è MC-42528. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
exl-id: 8bb29f43-92ae-4f37-b147-7121b55c185b
feature: Catalog Management, Categories, GraphQL, Customer Service
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MC-42528: la query GraphQL di categoryList mostra tutte le categorie

La patch MC-42528 risolve il problema in cui la query GraphQL di `categoryList` restituisce le categorie assegnate e non assegnate quando la categoria di navigazione di una particolare categoria è impostata su &quot;Nega&quot;. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4. L’ID della patch è MC-42528. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Query GraphQL di `categoryList` restituisce le categorie assegnate e non assegnate.

<u>Passaggi da riprodurre</u>:

1. Creare due categorie, CAT1 e CAT2, e assegnare alcuni prodotti a ciascuna categoria.
1. Crea un catalogo condiviso privato.
1. Crea un utente aziendale e assegnalo al catalogo condiviso creato.
1. Assegna CAT1 al catalogo personalizzato e imposta l’autorizzazione per la categoria su &quot;Consenti&quot; categoria di navigazione per il gruppo di clienti del catalogo privato.
1. Impostare l&#39;autorizzazione della categoria per CAT2 su &quot;Nega&quot; categoria di esplorazione per il gruppo di clienti del catalogo privato.
1. Esegui il `categoryList` o `categories` Query GraphQL come utente dell’azienda.

<u>Risultati previsti</u>:

Nella risposta viene visualizzato solo il CAT1.

<u>Risultati effettivi</u>:

Tutte le categorie vengono visualizzate nella risposta indipendentemente dalle autorizzazioni di navigazione della categoria.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sezione.
