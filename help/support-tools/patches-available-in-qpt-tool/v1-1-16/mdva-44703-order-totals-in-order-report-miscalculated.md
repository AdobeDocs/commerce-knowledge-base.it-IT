---
title: "MDVA-44703: i totali degli ordini nel rapporto Ordini non vengono calcolati correttamente"
description: La patch MDVA-44703 risolve il problema relativo al calcolo errato dei totali degli ordini nel rapporto Ordini per l'utente amministratore con restrizioni. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16. L'ID della patch è MDVA-44703. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.
exl-id: d8c31e47-ace6-4dba-a57c-941e722a6aad
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# MDVA-44703: i totali degli ordini nel rapporto Ordini non vengono calcolati correttamente

La patch MDVA-44703 risolve il problema relativo al calcolo errato dei totali degli ordini nel rapporto Ordini per l&#39;utente amministratore con restrizioni. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16. L&#39;ID della patch è MDVA-44703. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I totali degli ordini nel rapporto Ordini non vengono calcolati correttamente per l’utente amministratore con restrizioni.

<u>Passaggi da riprodurre</u>:

1. Crea un altro sito web con due store.
1. Crea un utente amministratore con restrizioni con accesso solo al nuovo sito web.
1. Accedi come utente amministratore con restrizioni.
1. Crea due ordini con totali diversi, uno per ogni nuovo negozio.
1. Creare le fatture per gli ordini.
1. Vai a **Rapporti** > **Vendite** e apri **Rapporto Ordini**.
1. Aggiorna statistiche.
1. Vedi il rapporto per ogni negozio.

<u>Risultati previsti</u>:

I totali delle vendite corrispondono all&#39;importo dell&#39;ordine di ciascun negozio.

<u>Risultati effettivi</u>:

Il totale aggregato delle vendite per l&#39;intero sito Web viene visualizzato per ogni negozio.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
