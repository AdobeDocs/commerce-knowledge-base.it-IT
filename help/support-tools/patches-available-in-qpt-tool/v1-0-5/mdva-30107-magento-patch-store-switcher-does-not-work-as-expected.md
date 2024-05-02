---
title: "MDVA-30107: il commutatore dell'archivio non funziona come previsto"
description: La patch MDVA-30107 risolve il problema relativo al funzionamento imprevisto del commutatore dello store se vengono utilizzati URL di base diversi per le visualizzazioni dello store. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5.
exl-id: feaef9ed-615f-4a0a-a7c5-1833f993d27f
feature: Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# MDVA-30107: il commutatore dell&#39;archivio non funziona come previsto

La patch MDVA-30107 risolve il problema relativo al funzionamento imprevisto del commutatore dello store se vengono utilizzati URL di base diversi per le visualizzazioni dello store. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5.

## Prodotti e versioni interessati

* Adobe Commerce on-premise 2.3.0 - 2.3.5.x
* Adobe Commerce sull’infrastruttura cloud 2.3.0 - 2.3.5.x

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando un utente passa da un archivio all’altro utilizzando il commutatore archivio, la richiesta non riesce se l’URL di base dell’archivio di destinazione è diverso.

<u>Passaggi da riprodurre</u>:

1. Crea due o più archivi con URL di base diversi.
1. Vai a una pagina di categoria in una vetrina di uno qualsiasi di questi negozi.
1. Provare a passare all&#39;altro punto vendita utilizzando il commutatore store.

<u>Risultati previsti</u>:

Ti reindirizzano a una pagina simile dell’altro store.

<u>Risultati effettivi</u>:

Ti reindirizzano alla home page dello stesso negozio.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
