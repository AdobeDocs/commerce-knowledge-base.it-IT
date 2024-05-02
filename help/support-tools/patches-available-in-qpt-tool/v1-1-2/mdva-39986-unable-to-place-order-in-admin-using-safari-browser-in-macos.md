---
title: "MDVA-39986: impossibile effettuare ordini in amministratore nel browser Safari su macOS"
description: La patch MDVA-39986 risolve il problema che impediva agli utenti di effettuare ordini nell'amministratore utilizzando il browser Safari su macOS. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.2. L'ID della patch è MDVA-39986. Il problema è stato risolto in Adobe Commerce 2.4.3.
exl-id: a35b6253-e03f-4bdb-a3a3-fceb70588c6e
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# MDVA-39986: impossibile effettuare ordini in amministratore nel browser Safari su macOS

La patch MDVA-39986 risolve il problema che impediva agli utenti di effettuare ordini nell&#39;amministratore utilizzando il browser Safari su macOS. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.2. L&#39;ID della patch è MDVA-39986. Il problema è stato risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1 - 2.4.2-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli utenti non possono effettuare ordini presso l’amministratore utilizzando il browser Safari su macOS.

<u>Passaggi da riprodurre</u>:

1. Effettua un ordine.
1. Vai all’amministratore tramite il browser Safari su macOS e apri l’ordine creato in precedenza.
1. Fai clic su **Riordina**.
1. Prova ad aggiornare **Quantità prodotto**.

<u>Risultati previsti</u>:

Gli utenti devono essere in grado di riordinare il file utilizzando il browser Safari su macOS.

<u>Risultati effettivi</u>:

Gli utenti ricevono un errore JS in cui viene visualizzata la rotellina che viene eseguita all’infinito.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
