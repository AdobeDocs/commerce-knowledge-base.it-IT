---
title: "MDVA-39043: errore restituito dagli utenti amministratori durante l'aggiunta del widget alla pagina CMS"
description: La patch MDVA-39043 risolve il problema che causava un errore agli utenti amministratori con accesso limitato durante l'aggiunta del widget "Prodotti" alla pagina CMS. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.2. L'ID della patch è MDVA-39043. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
exl-id: 63057351-e972-4575-9bf0-e818f590b40a
feature: Admin Workspace, CMS, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# MDVA-39043: errore restituito dagli utenti amministratori durante l&#39;aggiunta del widget alla pagina CMS

La patch MDVA-39043 risolve il problema che causava un errore agli utenti amministratori con accesso limitato durante l&#39;aggiunta del widget &quot;Prodotti&quot; alla pagina CMS. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.2. L&#39;ID della patch è MDVA-39043. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.4 - 2.4.3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli utenti amministratori con accesso limitato ricevono un errore durante l’aggiunta del widget &quot;Prodotti&quot; alla pagina CMS.

<u>Passaggi da riprodurre</u>:

1. Accedi al backend utilizzando l’amministratore con accesso solo per la modifica del contenuto.
1. Vai a **Contenuto** > **Pagine**.
1. Apri una pagina da modificare.
1. Modifica il contenuto con **Page Builder**.
1. Aggiungi **Prodotto** widget da **Aggiungi contenuto** sezione.
1. Clic **Configura** il **Prodotto** widget.

<u>Risultati previsti</u>:

Non viene visualizzato alcun errore.

<u>Risultati effettivi</u>:

Viene ricevuto il seguente messaggio di errore:

`*A technical problem with the server created an error. Try again to continue what you were doing. If the problem persists, try again later.*`

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
