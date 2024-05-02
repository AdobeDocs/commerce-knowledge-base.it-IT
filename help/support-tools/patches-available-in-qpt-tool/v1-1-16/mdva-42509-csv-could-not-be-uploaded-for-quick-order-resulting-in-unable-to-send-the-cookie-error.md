---
title: '"MDVA-42509: impossibile caricare il file CSV per l’ordine rapido. Errore "Impossibile inviare il cookie"'
description: La patch MDVA-42509 risolve il problema che impediva il caricamento di un file CSV per l'ordine rapido, causando l'errore *Impossibile inviare il cookie*. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16. L'ID della patch è MDVA-42509. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: 7aa0e710-9a28-4531-b9cb-c82f654487f4
feature: B2B, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# MDVA-42509: impossibile caricare il file CSV per l’ordine rapido. Errore &quot;Impossibile inviare il cookie&quot;

La patch MDVA-42509 risolve il problema che impediva il caricamento di un file CSV per l&#39;ordine rapido, con il risultato di *Impossibile inviare il cookie* errore. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16. L&#39;ID della patch è MDVA-42509. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.3 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando si crea un ordine rapido con un numero elevato di prodotti utilizzando un file CSV, viene visualizzato un errore di cookie: *Impossibile inviare il cookie*

<u>Passaggi da riprodurre</u>:

1. Abilita Ordine rapido passando a **Negozi** > **Impostazioni** > **Configurazioni** > **Generale** > **Caratteristiche B2B**.
1. Creare un account cliente e passare a **Ordine rapido** nel collegamento superiore.
1. Prova a creare un ordine rapido utilizzando un file CSV con più di 100 SKU.

<u>Risultati previsti</u>:

Puoi creare un ordine rapido con un numero elevato di SKU.

<u>Risultati effettivi</u>:

Viene visualizzato un messaggio di errore relativo alla dimensione del cookie.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
