---
title: "MDVA-30945: errore irreversibile durante le operazioni di aggiunta e aggiornamento del carrello"
description: La patch MDVA-30945 risolve il problema che causa un errore irreversibile *Chiamata a una funzione membro getValue() su null in Module-configurable-product CartItemProcessor.php* durante l'aggiornamento dei carrelli. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7. Il problema è stato risolto in Adobe Commerce 2.4.2.
exl-id: 0950e91b-900b-421d-91e7-abbfca4f30be
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# MDVA-30945: errore irreversibile durante le operazioni di aggiunta e aggiornamento del carrello

La patch MDVA-30945 risolve il problema che causa un errore irreversibile *Chiamata a una funzione membro getValue() su null in Module-configurable-product CartItemProcessor.php* durante l&#39;aggiornamento dei carrelli. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7. Il problema è stato risolto in Adobe Commerce 2.4.2.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Un errore PHP irreversibile dopo l’aggiornamento dei prodotti nel carrello in Admin.

<u>Passaggi da riprodurre</u>:

1. In Commerce Admin, crea un prodotto configurabile senza opzioni.
1. Aggiungilo al carrello nella vetrina.
1. Torna a Amministratore, aggiungi opzioni configurabili al prodotto e salva le modifiche.
1. Aggiorna la pagina del carrello nella vetrina.

<u>Risultati previsti</u>:

Nella pagina del carrello viene visualizzato il seguente messaggio di convalida: *Alcuni dei prodotti seguenti non dispongono di tutte le opzioni richieste*.

<u>Risultati effettivi</u>:

La pagina del carrello è vuota. Nel PHP `error.log` viene registrato il seguente errore: *Eccezione non rilevata &#39;Error&#39; con messaggio &#39;Call to a member function getValue() on null&#39; in vendor/magento/module-configurable-product/Model/Quote/Item/CartItemProcessor.php:76*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
