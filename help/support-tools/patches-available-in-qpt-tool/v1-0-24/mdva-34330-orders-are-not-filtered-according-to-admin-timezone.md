---
title: "MDVA-34330: ordini non filtrati in base al fuso orario dell'amministratore"
description: La patch MDVA-34330 risolve il problema che non consente di filtrare gli ordini in base al fuso orario dell'amministratore. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24. L'ID della patch è MDVA-34330. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.3.
exl-id: cb369ee3-60b0-4317-a448-0c4ed64f2816
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# MDVA-34330: ordini non filtrati in base al fuso orario dell&#39;amministratore

La patch MDVA-34330 risolve il problema che non consente di filtrare gli ordini in base al fuso orario dell&#39;amministratore. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24. L&#39;ID della patch è MDVA-34330. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.4.1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i tipi di distribuzione) 2.3.1 - 2.4.2-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Ordini non filtrati in base al fuso orario dell’amministratore.

<u>Passaggi da riprodurre</u>:

1. Vai a **Negozi** > Impostazioni > **Configurazione** > **Generale** e imposta **Fuso orario** a *Ora solare fuso orientale (America/New_York)*
1. Effettua un nuovo ordine dopo le 00:00 UTC
1. Vai a **Vendite** > **Ordini** e filtrare per data odierna


<u>Risultati previsti</u>:

L’ordine effettuato oggi dopo le 00:00 UTC è visibile nei risultati filtrati.

<u>Risultati effettivi</u>:

Ordine mancante nei risultati filtrati.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti a seconda del tipo di distribuzione:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sezione.
