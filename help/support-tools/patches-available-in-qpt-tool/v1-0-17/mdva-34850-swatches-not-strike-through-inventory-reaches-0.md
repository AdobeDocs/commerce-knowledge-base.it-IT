---
title: '''MDVA-34850: l''inventario dei campioni non barrati raggiunge "0"'''
description: La patch MDVA-34850 risolve il problema se i campioni non vengono suddivisi quando l'inventario raggiunge il valore "0" e non sono visibili nel collegamento della pagina dettagli prodotto (PDP) a nessun altro campione di magazzino. Anche **Display Out-of-Stock Products** (Visualizza prodotti esauriti) è impostato su *Yes* nella configurazione amministratore. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17. Il problema è stato risolto in Adobe Commerce 2.4.3.
exl-id: 90f5cef4-137a-426d-a447-2d1aca23e6c1
feature: Inventory, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 0%

---

# MDVA-34850: l&#39;inventario dei campioni non barrati raggiunge &quot;0&quot;

La patch MDVA-34850 risolve il problema se i campioni non vengono suddivisi quando l&#39;inventario raggiunge il valore &quot;0&quot; e non sono visibili nel collegamento della pagina dettagli prodotto (PDP) a nessun altro campione di magazzino. Il **Visualizza prodotti esauriti** è impostato anche su *Sì* in configurazione amministratore. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17. Il problema è stato risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.5-p2

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce on-premise e Adobe Commerce sull’infrastruttura cloud 2.3.1 - 2.4.2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le opzioni di prodotto esaurite non vengono visualizzate nella pagina PDP quando le scorte di magazzino predefinite non sono in uso e **Visualizza prodotti esauriti** la configurazione è abilitata.

<u>Prerequisiti</u>:

* Installare MSI (Multi-Source Inventory).
* Abilitare la visualizzazione dei prodotti esauriti in [Opzioni scorte](https://docs.magento.com/user-guide/configuration/catalog/inventory.html).

<u>Passaggi da riprodurre</u>:

1. Crea un nuovo magazzino \[Nuovo magazzino\], assegnandogli tutti i siti web e l’origine di cui sopra. Ora il titolo predefinito non deve essere in uso.
1. Creare un [prodotto configurabile](https://docs.magento.com/user-guide/catalog/product-create-configurable.html) aggiunta di tre opzioni di dimensione \[S,M,L\].
1. Apri ciascuna opzione e aggiungi le quantità assegnando solo l’origine personalizzata \[new\_source\] creata. Inoltre, imposta \[Stato origine\] su \[In magazzino\].
1. Reindicizza e controlla il prodotto configurabile dal front-end. Tutte e tre le opzioni devono essere visibili.
1. Aprire un prodotto semplice assegnato a \[size:S\] dal backend e impostare \[Stato origine\] su \[Esaurito\]. Aggiornare inoltre la quantità a 0. Reindicizza e controlla il prodotto configurabile dal front-end.

<u>Risultati previsti</u>:

Poiché l’opzione Visualizza prodotti esauriti è abilitata, tutte e tre le opzioni devono essere visualizzate. L&#39;opzione esaurita \[S\] deve essere disabilitata ed eliminata. Dovrebbe visualizzare 2 x di 1 prodotto opzione con prezzo = 12x2, nell’ordine dei dettagli sul front-end e sul back-end.

<u>Risultati effettivi</u>:

L&#39;opzione Esaurito è nascosta.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sezione.
