---
title: "Patch MDVA-31969: importazione di prodotti con immagini .csv duplicate"
description: La patch MDVA-31969 risolve il problema della duplicazione delle immagini durante l'importazione di due prodotti con estensione csv. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.14.
exl-id: 2a3c9cce-1f71-4f27-807e-12beffc379d2
feature: Data Import/Export, Products
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Patch MDVA-31969: importazione di prodotti con immagini .csv duplicate

La patch MDVA-31969 risolve il problema della duplicazione delle immagini durante l&#39;importazione di due prodotti con estensione csv. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.14.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.4-p2

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce su infrastruttura cloud e Adobe Commerce on-premise 2.3.3 - 2.3.4-p2, 2.4.0 - 2.4.1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le nuove immagini dei prodotti vengono create in `pub/media` cartella, anche se la stessa immagine esiste già, durante l’importazione dei prodotti.

<u>Passaggi da riprodurre</u>:

1. Creare una directory per le immagini: `mkdir var/import-images`
1. Aggiungi immagini nel percorso `<install dir>/var/import-images`.
1. Importa il file .csv del prodotto due volte.

<u>Risultati previsti</u>:

I prodotti finiscono con l&#39;immagine di ogni prodotto allegata una volta.

<u>Risultati effettivi</u>:

I prodotti finiscono con immagini di prodotto duplicate.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
