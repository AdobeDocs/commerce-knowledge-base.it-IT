---
title: "MDVA-34102: quantità vendibile incoerente"
description: La patch MDVA-34102 risolve il problema se la quantità di scorte predefinite è zero per i prodotti disabilitati nelle pagine Griglia prodotto e Modifica prodotto nell'amministratore. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18. L'ID della patch è MDVA-34102. Il problema è pianificato per la risoluzione in Adobe Commerce versione 2.4.3.
exl-id: cb1d4689-c122-4afd-8597-b2627027aaf3
feature: Variables
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MDVA-34102: quantità vendibile incoerente

La patch MDVA-34102 risolve il problema se la quantità di scorte predefinite è zero per i prodotti disabilitati nelle pagine Griglia prodotto e Modifica prodotto nell&#39;amministratore. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18. L&#39;ID della patch è MDVA-34102. Il problema è pianificato per la risoluzione in Adobe Commerce versione 2.4.3.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.5-p2

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce on-premise e Adobe Commerce sull’infrastruttura cloud 2.3.0-2.4.2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Passaggi da riprodurre</u>:

1. Imposta due siti Web con store e visualizzazioni store.
1. Create un&#39;origine e un magazzino aggiuntivi.
1. Aggiungi un prodotto semplice:
   * Imposta **Abilita prodotto** = *No*.
   * Assegna due origini con **Stato elemento di origine** = *In magazzino* con una quantità maggiore di zero (ad esempio: **azioni di default** = *123* e **Stock del Regno Unito** = *123*).
1. Salva il prodotto.
1. Controlla la **Quantità vendibile prodotto** scheda.

<u>Risultati previsti</u>:

Sia le scorte di default che quelle del Regno Unito = *123*

La quantità di scorte predefinite viene visualizzata correttamente per i prodotti disabilitati nelle pagine Griglia prodotto e Modifica prodotto nell’Amministratore.

<u>Risultati effettivi</u>:

Stock di default = *0* e le scorte nel Regno Unito = *123*

La quantità di scorte predefinite è zero per i prodotti disabilitati nelle pagine Griglia prodotto e Modifica prodotto nell’amministratore.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili nello strumento QPT, consultare [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sezione.
