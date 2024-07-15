---
title: "MDVA-30428: lista dei desideri non funzionante con Inventory management"
description: La patch MDVA-30428 risolve la lista dei desideri che non funzionano con Inventory management (MSI). Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5.
exl-id: 79e8d5d6-b073-48cf-8ecc-5c44667c12ad
feature: Inventory, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# MDVA-30428: lista dei desideri non funzionante con Inventory management

La patch MDVA-30428 risolve la lista dei desideri che non funzionano con Inventory management (MSI). Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.3 - 2.3.3-p1 (QPT 1.0.6) e 2.3.5 - 2.4.1 (QPT 1.0.5)

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando si aggiunge un prodotto alla lista dei desideri, quando il prodotto viene assegnato a un&#39;origine inventario personalizzata, viene visualizzato il seguente messaggio: &quot;*Impossibile aggiungere l&#39;elemento alla lista dei desideri al momento: impossibile aggiungere il prodotto senza scorte alla lista dei desideri.*&quot;

<u>Passaggi da riprodurre</u>:

1. Crea una nuova origine inventario in Commerce Admin. Per i passaggi, consulta [Catalogo > Aggiunta di un nuovo Source](https://docs.magento.com/user-guide/catalog/inventory-sources-add.html?itm_source=merchdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=new%20inventory%20source) nella nostra guida utente.
1. Crea un nuovo inventario di magazzino in Commerce Admin, assegna la nuova origine e il sito Web predefinito al nuovo magazzino. Per i passaggi, consulta [Catalogo > Aggiunta di un nuovo Stock](https://docs.magento.com/user-guide/catalog/inventory-stock-add.html#add-new-stock) nella nostra guida utente.
1. Crea un prodotto semplice e assegna le nuove scorte solo come scorte.
1. Visita la pagina dei dettagli dei prodotti semplici nel front-end.
1. Aggiungere il prodotto alla lista dei desideri. Viene visualizzato il seguente errore: *Impossibile aggiungere l&#39;elemento alla lista dei desideri al momento: impossibile aggiungere il prodotto senza scorte alla lista dei desideri*.

<u>Risultati previsti</u>:

Il prodotto deve essere aggiunto alla lista dei desideri con il magazzino personalizzato.

<u>Risultati effettivi</u>:

Il prodotto non viene aggiunto alla lista dei desideri e viene visualizzato un messaggio di errore.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
