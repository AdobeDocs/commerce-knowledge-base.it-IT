---
title: "MDVA-37082: indice parziale non corretto dello stato delle scorte per i prodotti raggruppati"
description: La patch del Magento MDVA-37082 risolve il problema quando l'indice parziale dello stato delle scorte per i prodotti raggruppati non è corretto per le scorte personalizzate. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25. L'ID della patch è MDVA-37082. Il problema è pianificato per essere risolto nel Magento 2.4.4.
exl-id: 1c0abc99-bd24-4848-87a3-227a63655cb7
feature: Cache, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---

# MDVA-37082: indice parziale non corretto dello stato delle scorte per i prodotti raggruppati

La patch del Magento MDVA-37082 risolve il problema quando l&#39;indice parziale dello stato delle scorte per i prodotti raggruppati non è corretto per le scorte personalizzate. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25. L&#39;ID della patch è MDVA-37082. Il problema è pianificato per essere risolto nel Magento 2.4.4.


## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**
Adobe Commerce sull’infrastruttura cloud 2.3.4-p2

**Compatibile con le versioni di Adobe Commerce:**
Adobe Commerce on-premise e Adobe Commerce sull’infrastruttura cloud 2.3.0-2.4.2-p1
>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’indicizzazione incrementale di prodotti secondari di prodotti raggruppati può causare l’indicizzazione errata di altri prodotti raggruppati quando gli elementi secondari vengono condivisi.

<u>Passaggi da riprodurre</u>:

* Crea un nuovo stock e una nuova origine per il sito Web principale.
* Creare 3 prodotti semplici con qtà 10,15 e 0.
* Creare 2 prodotti raggruppati e assegnare il primo prodotto semplice con qtà 10 a uno e altri 2 prodotti semplici all&#39;altro.
* Verifica che entrambi i prodotti raggruppati possano essere accessibili dal front-end, a magazzino.
* Assegnare il prodotto semplice con qtà 0 ai prodotti up-sell del primo prodotto raggruppato.
* Pulisci la cache dell’intera pagina e controlla il secondo prodotto raggruppato dal front-end.
* Esegui una reindicizzazione completa.
* Controlla il secondo prodotto raggruppato dal front-end.
* Salvare il primo prodotto raggruppato.
* Pulisci la cache a tutta pagina e controlla il secondo prodotto raggruppato dal front-end.

<u>Risultati previsti</u>:

Il prodotto raggruppato non è esaurito dopo aver salvato un altro prodotto raggruppato con l&#39;up-sell. Il problema viene risolto dopo una reindicizzazione completa.

<u>Risultati effettivi</u>:

Il secondo prodotto raggruppato non è disponibile quando si salva il primo prodotto raggruppato.

## Applicare la patch

Per applicare singole patch, utilizza i seguenti collegamenti alla documentazione per gli sviluppatori, a seconda del metodo di implementazione di Adobe Commerce:

* Adobe Commerce on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento Quality Patches: è stato introdotto un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Verifica se la patch è disponibile per il problema del Magento utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Per informazioni sulle altre patch disponibili nello strumento QPT, fare riferimento alla sezione [Patch disponibili nello strumento QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
