---
title: "MDVA-41061: lo stato del magazzino viene reimpostato su vendibile quando il prodotto viene salvato da Admin"
description: La patch MDVA-41061 risolve il problema se lo stato delle scorte viene reimpostato su vendibile quando il prodotto viene salvato dall'amministratore. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.5. L'ID della patch è MDVA-41061. La versione più recente della patch è disponibile in QPT 1.1.15 con ID di patch MDVA-41061-V3. Tieni presente che il problema è risolto in Adobe Commerce 2.4.4.
exl-id: fd71d3e5-685f-4987-b7e7-bfd86810d865
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# MDVA-41061: lo stato del magazzino viene reimpostato su vendibile quando il prodotto viene salvato dall&#39;amministratore

La patch MDVA-41061 risolve il problema se lo stato delle scorte viene reimpostato su vendibile quando il prodotto viene salvato dall&#39;amministratore. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.5. L&#39;ID della patch è MDVA-41061. La versione più recente della patch è disponibile in QPT 1.1.15 con ID di patch MDVA-41061-V3. Tieni presente che il problema è risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.2-p2, 2.4.3 - 2.4.3-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Lo stato delle scorte viene reimpostato su vendibile quando il prodotto viene salvato dall’amministratore.

<u>Prerequisiti</u>:

I moduli di inventario sono installati.

<u>Passaggi da riprodurre</u>:

1. Creare un prodotto semplice con Qtà = 1.
1. Effettuare un ordine utilizzando il prodotto creato nel passaggio 1.
1. Esegui cron: assicurati `inventory.reservations.updateSalabilityStatus` la coda viene eseguita e lo stato delle scorte di prodotto è stato modificato in zero nel `cataloginventory_stock_status` tabella.
1. Controlla il prodotto sul front-end. Deve essere contrassegnato come **Esaurito**.
1. Salva il prodotto nell’amministratore senza apportare modifiche.

<u>Risultati previsti</u>:

* Lo stato dello stock non deve essere aggiornato.
* Il prodotto deve essere **Esaurito** sul fronte.

<u>Risultati effettivi</u>:

* Il prodotto semplice è contrassegnato come **In magazzino** sul fronte.
* Utenti ottengono *La quantità richiesta non è disponibile* quando tenta di aggiungerlo al carrello.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
