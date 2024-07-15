---
title: "MDVA-28651: B2B - virgolette lente da caricare"
description: La patch MDVA-28651 risolve il problema relativo alle prestazioni quando si verificano diversi problemi di caricamento delle virgolette. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.9. Il problema era pianificato per essere risolto nella versione 2.4.2 di Adobe Commerce.
exl-id: 2d0bfbba-cdf3-4f9e-a900-ce42909fac8e
feature: B2B, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# MDVA-28651: B2B - preventivi lenti da caricare

La patch MDVA-28651 risolve il problema relativo alle prestazioni quando si verificano diversi problemi di caricamento delle virgolette. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.9. Il problema era pianificato per essere risolto nella versione 2.4.2 di Adobe Commerce.

## Prodotti e versioni interessati

* La patch è stata progettata per Adobe Commerce sull’infrastruttura cloud 2.3.4.
* La patch è compatibile anche con le seguenti versioni di Adobe Commerce: Adobe Commerce on-premise e Adobe Commerce on cloud infrastructure 2.3.0-2.3.5-p1, 2.4.0 e 2.4.1.

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Problemi di prestazioni nella pagina dell&#39;elenco di offerte cliente:

* doppio caricamento dell&#39;elenco di preventivo: primo con pagina intera, secondo con richiesta Ajax.
* un ciclo di caricamento di ciascuna virgoletta dal plug-in.
* doppio caricamento delle voci del preventivo quando il preventivo è stato convertito nell&#39;istantanea.

<u>Passaggi da riprodurre</u>

1. Assegnazione di più di 40 preventivi a un cliente.
1. Accedi e sfoglia la pagina **Le mie citazioni**.

<u>Risultato effettivo</u>

Il tempo di risposta per caricare completamente il contenuto della pagina **Le mie quotazioni** (caricamento della pagina + dati visualizzati nella griglia) è di ~ 45 secondi.

<u>Risultato previsto</u>

Il tempo di risposta per il caricamento completo del contenuto della pagina **Le mie quotazioni** deve essere inferiore a 45 secondi.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
