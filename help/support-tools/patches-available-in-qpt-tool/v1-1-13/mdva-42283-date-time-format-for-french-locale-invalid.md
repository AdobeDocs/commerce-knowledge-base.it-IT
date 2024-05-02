---
title: "MDVA-42283: il formato data-ora per le impostazioni locali francesi non è valido"
description: La patch MDVA-42283 risolve il problema che causa la mancata validità del formato data/ora nella griglia dell'ordine di amministrazione per le impostazioni internazionali in francese. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13. L'ID della patch è MDVA-42283. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: 9b470e7b-4b73-4100-9a9d-1a45a5ac628b
feature: CMS
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# MDVA-42283: il formato data-ora per le impostazioni locali francesi non è valido

La patch MDVA-42283 risolve il problema che causa la mancata validità del formato data/ora nella griglia dell&#39;ordine di amministrazione per le impostazioni internazionali in francese. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13. L&#39;ID della patch è MDVA-42283. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il formato data/ora nella griglia dell&#39;ordine di amministrazione per le impostazioni internazionali francesi non è valido.

<u>Passaggi da riprodurre</u>:

1. Crea un ordine, un cliente, una pagina CMS o un blocco CMS.
1. Vai a **Amministratore** > **Impostazioni account** e impostare le impostazioni locali dell&#39;interfaccia per l&#39;amministratore su **Français (Canada)**/**français (Canada)(fr_CA)** o **Portoghese brasiliano (pt_BR)**.
1. Osservare il valore nella colonna data per qualsiasi ordine, spedizione, nota di credito, cliente, pagina CMS o griglia di blocchi CMS.

<u>Risultati previsti</u>:

La data è nel formato visualizzato nella pagina di modifica effettiva per l’entità.

<u>Risultati effettivi</u>:

Il valore data-ora non è corretto.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
