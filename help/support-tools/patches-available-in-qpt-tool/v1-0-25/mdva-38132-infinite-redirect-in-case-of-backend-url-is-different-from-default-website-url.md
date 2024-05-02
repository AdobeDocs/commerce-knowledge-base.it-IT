---
title: "MDVA-38132: reindirizzamento infinito quando l'URL del back-end è diverso dall'URL del sito Web predefinito"
description: La patch MDVA-38132 risolve il problema del reindirizzamento infinito quando l'URL del back-end è diverso da quello predefinito del sito Web. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25. L'ID della patch è MDVA-38132. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.3.
exl-id: 122145d7-0961-47f8-8ab6-a15d62996e49
feature: Cache
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# MDVA-38132: reindirizzamento infinito quando l&#39;URL del back-end è diverso dall&#39;URL del sito Web predefinito

La patch MDVA-38132 risolve il problema del reindirizzamento infinito quando l&#39;URL del back-end è diverso da quello predefinito del sito Web. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25. L&#39;ID della patch è MDVA-38132. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**
Adobe Commerce sull’infrastruttura cloud 2.3.4-p2

**Compatibile con le versioni di Adobe Commerce:**
Adobe Commerce (tutti i metodi di implementazione) 2.3.3-2.4.2-p1
>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il pannello di amministrazione di Commerce ha un reindirizzamento infinito quando l’URL del back-end è diverso dall’URL del sito web predefinito.

<u>Prerequisiti</u>:

* L’URL di base viene utilizzato sia per il backend che per la vetrina. L&#39;URL di base protetto non è utilizzato.
* Il server web è configurato in modo che Adobe Commerce sia accessibile tramite due URL diversi. L’URL1 viene utilizzato per l’installazione di Adobe Commerce.

<u>Passaggi da riprodurre</u>:

1. Vai a Pannello di amministrazione > **Negozi** > **Configurazione** > **Web**.
1. Lascia l’URL di base originale nella configurazione globale. È il tuo URL1.
1. Passa all’ambito del sito web principale.
1. Modifica l’URL di base in un URL diverso (consulta le precondizioni per configurare correttamente il server web). Questo è il tuo URL2.
1. Cancellare la cache (se necessario e possibile).
1. Apri il pannello di amministrazione.

<u>Risultati previsti</u>:

Il pannello di amministrazione è stato aperto e può essere navigato. Lo store del sito Web principale è stato aperto e può essere visitato.

<u>Risultati effettivi</u>:

Si verifica un reindirizzamento infinito. Adobe Commerce reindirizza dall’URL1 all’URL2 e continua avanti e indietro.

## Applicare la patch

Per applicare singole patch, utilizzare i seguenti collegamenti in base al prodotto Adobe Commerce:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili nello strumento QPT, consultare [Patch disponibili nello strumento QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sezione.
