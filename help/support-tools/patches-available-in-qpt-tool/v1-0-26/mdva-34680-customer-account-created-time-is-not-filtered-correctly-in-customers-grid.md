---
title: "MDVA-34680: l'account del cliente non viene filtrato correttamente nella griglia del cliente"
description: La patch MDVA-34680 risolve il problema quando l'account cliente creato dopo le 00:00 UTC non viene filtrato correttamente nella griglia dei clienti. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26. L'ID della patch è MDVA-34680. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.3.
exl-id: 2e506d7a-8cde-41eb-84b2-1a5ff8015428
feature: Customer Service
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# MDVA-34680: l&#39;account del cliente non viene filtrato correttamente nella griglia del cliente

La patch MDVA-34680 risolve il problema quando l&#39;account cliente creato dopo le 00:00 UTC non viene filtrato correttamente nella griglia dei clienti. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26. L&#39;ID della patch è MDVA-34680. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.4.1 e 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce on-premise e Adobe Commerce sull’infrastruttura cloud 2.3.6-2.3.7 e 2.4.1-2.4.2-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando un account cliente viene creato dopo le 00:00 UTC e si tenta di filtrare gli account entro tale data, non restituirà il cliente.

<u>Passaggi da riprodurre</u>:

1. Vai a **Negozi** > **Configurazione** > **Generale** e imposta il fuso orario su Eastern Standard [Stati Uniti/New York].
1. Crea un nuovo account cliente dopo le 00:00 UTC.
1. Vai a **Clienti** > **Tutti i clienti** e filtrare gli account in base alla data odierna.

<u>Risultati previsti</u>:

I filtri dell’account del cliente mostrano il nuovo account creato oggi dopo le 00:00 UTC.

<u>Risultati effettivi</u>:

I filtri account cliente non mostrano il nuovo account creato oggi.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sezione.
