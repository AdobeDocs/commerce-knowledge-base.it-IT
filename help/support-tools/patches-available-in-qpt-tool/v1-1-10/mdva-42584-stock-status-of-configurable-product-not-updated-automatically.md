---
title: "MDVA-42584: lo stato del magazzino del prodotto configurabile non viene aggiornato automaticamente"
description: La patch MDVA-42584 risolve il problema se lo stato delle scorte del prodotto configurabile non viene aggiornato automaticamente quando il prodotto semplice viene aggiornato. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10. L'ID della patch è MDVA-42584. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: bf2697a2-8d15-408b-8d59-7b4173537e60
feature: Configuration, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# MDVA-42584: lo stato del magazzino del prodotto configurabile non viene aggiornato automaticamente

La patch MDVA-42584 risolve il problema se lo stato delle scorte del prodotto configurabile non viene aggiornato automaticamente quando il prodotto semplice viene aggiornato. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10. L&#39;ID della patch è MDVA-42584. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Lo stato del magazzino del prodotto configurabile nel back-end non viene aggiornato automaticamente quando il relativo prodotto semplice è impostato su **In magazzino** tramite API o importazione.

<u>Prerequisiti</u>:

MSI installato.

<u>Passaggi da riprodurre</u>:

1. Creare un prodotto configurabile **ControlloInv001**, con due opzioni: **InvCheck001-M** e **ControlloInv001-L**.
1. Entrambi i prodotti semplici devono avere una quantità ed essere **In magazzino** in modo che il prodotto configurabile **In magazzino** nel backend.
1. Ora è possibile aggiornare sia i prodotti semplici che impostare Quantità su **0** e stato del magazzino a **Esaurito**.
1. Aggiorna il prodotto configurabile e verifica che lo stato delle scorte sia aggiornato a **Esaurito**.
1. Utilizza il seguente endpoint API e imposta il prodotto semplice **InvCheck001-M** a **In magazzino** con Quantità > 0.

   ```JSON
   /rest/V1/inventory/source-items
   
   {
     "sourceItems":
     [
       {
         "sku": "InvCheck001-M",
         "source_code": "default",
         "quantity": 10,
         "status": 1
       }
     ]
   }
   ```

1. Vai al backend e verifica lo stato di quantità e scorte del prodotto semplice **InvCheck001-M**. Viene aggiornato a **In magazzino**.
1. Aggiorna il prodotto configurabile e controlla lo stato delle scorte.

<u>Risultati previsti</u>:

Stato del magazzino del prodotto configurabile **ControlloInv001** nel backend viene aggiornato automaticamente in **In magazzino**.

<u>Risultati effettivi</u>:

Lo stato delle scorte del prodotto configurabile è ancora **Esaurito**.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
