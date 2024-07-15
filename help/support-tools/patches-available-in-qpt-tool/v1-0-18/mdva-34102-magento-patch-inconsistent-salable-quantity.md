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

La patch MDVA-34102 risolve il problema se la quantità di scorte predefinite è zero per i prodotti disabilitati nelle pagine Griglia prodotto e Modifica prodotto nell&#39;amministratore. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18. L&#39;ID della patch è MDVA-34102. Il problema è pianificato per la risoluzione in Adobe Commerce versione 2.4.3.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.5-p2

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce on-premise e Adobe Commerce sull’infrastruttura cloud 2.3.0-2.4.2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Passaggi da riprodurre</u>:

1. Imposta due siti Web con store e visualizzazioni store.
1. Create un&#39;origine e un magazzino aggiuntivi.
1. Aggiungi un prodotto semplice:
   * Imposta **Abilita prodotto** = *No*.
   * Assegna due origini con **Stato elemento Source** = *In magazzino* con una quantità maggiore di zero (ad esempio: **azioni predefinite** = *123* e **azioni UK** = *123*).
1. Salva il prodotto.
1. Controlla la scheda **Quantità venduta prodotto**.

<u>Risultati previsti</u>:

Sia le azioni predefinite che quelle del Regno Unito = *123.*

La quantità di scorte predefinite viene visualizzata correttamente per i prodotti disabilitati nelle pagine Griglia prodotto e Modifica prodotto nell’Amministratore.

<u>Risultati effettivi</u>:

Le scorte predefinite = *0* e quelle del Regno Unito = *123.*

La quantità di scorte predefinite è zero per i prodotti disabilitati nelle pagine Griglia prodotto e Modifica prodotto nell’amministratore.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili nello strumento QPT, fare riferimento alla sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
