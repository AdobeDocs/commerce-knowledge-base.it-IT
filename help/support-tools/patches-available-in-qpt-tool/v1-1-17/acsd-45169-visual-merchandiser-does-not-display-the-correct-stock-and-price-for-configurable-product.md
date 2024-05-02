---
title: "ACSD-45169: Visual Merchandiser mostra azioni e prezzi non corretti per il prodotto configurabile"
description: La patch ACSD-45169 risolve il problema che causa la mancata visualizzazione da parte di Visual Merchandiser del prezzo e delle azioni corretti per un prodotto configurabile dopo l'applicazione di un aggiornamento di staging. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17. L’ID della patch è ACSD-45169. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.
exl-id: 5a7987c8-f276-4917-98f7-645402f4c454
feature: Categories, Configuration, Merchandising, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# ACSD-45169: Visual Merchandiser mostra azioni e prezzi errati per prodotti configurabili

La patch ACSD-45169 risolve il problema che causa la mancata visualizzazione da parte di Visual Merchandiser del prezzo e delle azioni corretti per un prodotto configurabile dopo l&#39;applicazione di un aggiornamento di staging. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17. L’ID della patch è ACSD-45169. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

In Visual Merchandiser non vengono visualizzati il prezzo e le azioni corretti per un prodotto configurabile dopo l&#39;applicazione di un aggiornamento di staging.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto semplice.
1. Crea qualsiasi aggiornamento pianificato per il prodotto semplice (è sufficiente disporre di ID di riga ed entità diversi).
1. Crea un prodotto configurabile.
1. Assegna il prodotto configurabile a una categoria.
1. Apri la categoria e osserva il prodotto configurabile nella sezione Visual Merchandiser.

<u>Risultati previsti</u>:

In Visual Merchandiser vengono visualizzati il titolo e il prezzo corretti.

<u>Risultati effettivi</u>:

In Visual Merchandiser vengono visualizzati un prezzo e un titolo errati.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
