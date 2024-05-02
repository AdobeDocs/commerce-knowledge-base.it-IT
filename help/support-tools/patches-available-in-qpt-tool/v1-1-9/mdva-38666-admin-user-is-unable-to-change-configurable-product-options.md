---
title: "MDVA-38666: l'utente amministratore non è in grado di modificare le opzioni di prodotto configurabili"
description: La patch MDVA-38666 risolve il problema che impediva all'utente amministratore di modificare le opzioni di prodotto configurabili nel carrello del cliente. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9. L'ID della patch è MDVA-38666. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: 72440e47-1deb-41da-a225-d4bc73029ad5
feature: Admin Workspace, Configuration, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# MDVA-38666: l&#39;utente amministratore non può modificare le opzioni di prodotto configurabili

La patch MDVA-38666 risolve il problema che impediva all&#39;utente amministratore di modificare le opzioni di prodotto configurabili nel carrello del cliente. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9. L&#39;ID della patch è MDVA-38666. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.4-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.2 - 2.3.5-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’utente amministratore non è in grado di modificare le opzioni di prodotto configurabili nel carrello del cliente.

<u>Passaggi da riprodurre</u>:

1. Imposta l&#39;ambito dell&#39;account cliente su Globale.
1. Crea due siti Web con negozi.
1. Crea due prodotti configurabili e assegnali a ciascun sito web.
1. Crea un account cliente in front-end e accedi.
1. Aggiungi un prodotto al carrello ed effettua un pagamento (questa operazione viene eseguita per rendere gli ID delle offerte diversi su ciascun sito web).
1. Aggiungi un prodotto al carrello e lascialo.
1. Passa al secondo sito Web e aggiungi il prodotto al carrello (lo stesso accesso dovrebbe funzionare, poiché l’ambito dell’account cliente è impostato su Globale).
1. Apri il cliente dall’amministratore e passa alla scheda carrello.
1. Passa dall’elenco a discesa e prova a modificare la configurazione.

<u>Risultati previsti</u>:

L’utente riceve una finestra a comparsa con opzioni configurabili.

<u>Risultati effettivi</u>:

Non viene visualizzato alcun modulo popup. L’utente non è in grado di modificare la configurazione.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
