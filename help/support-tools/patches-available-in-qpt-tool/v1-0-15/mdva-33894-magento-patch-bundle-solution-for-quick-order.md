---
title: "Patch MDVA-33894: soluzione bundle per ordine rapido"
description: La patch MDVA-33894 risolve diversi problemi relativi alla funzionalità di ordine rapido, tra cui l'aggiunta e la rimozione di più prodotti e la distinzione tra maiuscole e minuscole nello SKU. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.3.
exl-id: d0b18e71-5f48-441e-a8b9-c459f3d34599
feature: Cache, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# Patch MDVA-33894: soluzione bundle per ordine rapido

La patch MDVA-33894 risolve diversi problemi relativi alla funzionalità di ordine rapido, tra cui l&#39;aggiunta e la rimozione di più prodotti e la distinzione tra maiuscole e minuscole nello SKU. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch è stata creata per Adobe Commerce versione:** Adobe Commerce su infrastruttura cloud 2.4.0

**Compatibile con le versioni di Adobe Commerce:** Adobe Commerce su infrastruttura cloud e Adobe Commerce on-premise 2.4.0-2.4.1-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La patch MDVA-33894 è una soluzione bundle con correzioni per i seguenti problemi:

* **Il mio account** > **La funzionalità Ordina per SKU** fa distinzione tra maiuscole e minuscole: se si immette uno SKU valido ma la distinzione tra maiuscole e minuscole non è corretta (maiuscole e minuscole e così via), Adobe Commerce genera un errore.
* Quando un acquirente utilizza l’Ordine rapido per aggiungere più prodotti al carrello e tenta di rimuovere un prodotto, quest’ultimo non viene rimosso.
* Problemi di distinzione tra maiuscole e minuscole quando si aggiungono più SKU a un ordine in blocco.
* Problema di cache della pagina Ordine rapido con SKU precedentemente immessi.
* La quantità dell&#39;ordine rapido non viene riportata nel carrello.
* La duplicazione SKU non viene convalidata correttamente.

## Applicare la patch

Per applicare singole patch, utilizzare i seguenti collegamenti, a seconda del prodotto Adobe Commerce:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili nello strumento QPT, fare riferimento alla sezione [Patch disponibili nello strumento QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
