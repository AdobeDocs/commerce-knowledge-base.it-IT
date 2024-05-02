---
title: "MDVA-36718: le opzioni personalizzate rimangono dopo la modifica dell’API"
description: La patch di Magento MDVA-36718 risolve il problema quando le precedenti opzioni personalizzate rimangono dopo essere state modificate tramite API.
exl-id: e9755764-e563-4921-af75-a90e06237053
feature: REST
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---

# MDVA-36718: le opzioni personalizzate rimangono dopo la modifica dell&#39;API

La patch di Magento MDVA-36718 risolve il problema quando le precedenti opzioni personalizzate rimangono dopo essere state modificate tramite API.

Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22. L&#39;ID della patch è MDVA-36718. Il problema è pianificato per essere risolto nella versione 2.4.3 del Magento.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.4.1

**Compatibile con le versioni di Magento:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.0-2.4.2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto semplice.
1. Aggiungi un **tipo a discesa** opzione personalizzata.
1. Aggiorna l’opzione personalizzata tramite API: Send `PUT` richiesta a `/V1/products/options/{optionId}`.

<u>Risultati previsti</u>:

Le opzioni personalizzate vengono aggiornate come previsto.

<u>Risultati effettivi</u>:

Vengono aggiunte nuove opzioni personalizzate, ma rimangono quelle precedenti.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica la patch per il problema di Magento con lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili nello strumento QPT, consultare [Patch disponibili nello strumento QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sezione.
