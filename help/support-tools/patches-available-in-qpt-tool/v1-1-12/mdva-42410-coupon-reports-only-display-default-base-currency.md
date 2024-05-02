---
title: "MDVA-42410: nei rapporti coupon viene visualizzata solo la valuta di base predefinita"
description: La patch MDVA-42410 risolve il problema relativo alla visualizzazione della sola valuta di base nei rapporti coupon. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12. L'ID della patch è MDVA-42410. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: b442a2ce-1bd4-4f09-95fd-2c626e32f509
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-42410: nei report coupon viene visualizzata solo la valuta di base predefinita

La patch MDVA-42410 risolve il problema relativo alla visualizzazione della sola valuta di base nei rapporti coupon. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12. L&#39;ID della patch è MDVA-42410. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Nei rapporti coupon viene visualizzata solo la valuta di base predefinita.

<u>Passaggi da riprodurre</u>:

1. Crea un ulteriore sito Web, store e vista store.
1. Imposta una valuta diversa per il nuovo sito Web. Ad esempio, Euro.
1. Vai a **Negozi** > **Tassi di cambio** e configurare i tassi di valuta su **Euro**.
1. Creare un **Regola prezzo carrello** con una cedola specifica - **Test**.
1. Vai al front-end e effettua un ordine con **Test** coupon sul nuovo sito web.
1. Vai a **Rapporti** > **Vendite** > **Coupon**.
1. Seleziona il nuovo sito web nel menu a discesa Ambito.
1. Aggiornare le statistiche ed eseguire i rapporti.

<u>Risultati previsti</u>:

I rapporti coupon visualizzano la valuta del nuovo sito web come Euro.

<u>Risultati effettivi</u>:

La valuta di base predefinita (USD in questo caso) viene utilizzata nei rapporti coupon per il nuovo sito web.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
