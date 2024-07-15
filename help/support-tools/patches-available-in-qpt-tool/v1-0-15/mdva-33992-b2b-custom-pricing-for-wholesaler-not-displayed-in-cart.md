---
title: "MDVA-33992: prezzi personalizzati B2B per i grossisti non visualizzati nel carrello"
description: La patch MDVA-33992 risolve il problema che non riflette i prezzi personalizzati per un cliente B2B quando un prodotto viene aggiunto a un carrello. Questa patch è disponibile quando è installato QPT 1.0.15 (Quality Patches Tool). Il problema è pianificato per essere risolto in Adobe Commerce 2.4.3.
exl-id: 6018fae6-762c-46c6-9497-ecf090115b7f
feature: B2B, Catalog Management, Orders, Shopping Cart
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# MDVA-33992: prezzo personalizzato B2B per il grossista non visualizzato nel carrello

La patch MDVA-33992 risolve il problema che non riflette i prezzi personalizzati per un cliente B2B quando un prodotto viene aggiunto a un carrello. Questa patch è disponibile quando è installato QPT 1.0.15 (Quality Patches Tool). Il problema è pianificato per essere risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch è stata creata per Adobe Commerce versione:** Adobe Commerce su infrastruttura cloud 2.4.1 con B2B

**Compatibile con le versioni di Adobe Commerce:** Adobe Commerce su infrastruttura cloud e Adobe Commerce on-premise 2.3.0-2.4.1-p1 con B2B

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I prezzi personalizzati per un cliente B2B non vengono rispecchiati quando un prodotto viene aggiunto a un carrello.

<u>Passaggi da riprodurre</u>:

Il problema è riproducibile per la versione B2B con Shared Catalog abilitato.

1. Crea un’azienda B2B a cui è assegnato un catalogo condiviso personalizzato.
1. Crea un prodotto nel catalogo personalizzato dell’azienda con un prezzo personalizzato (prezzo livello).
1. In qualità di cliente B2B, verifica che il prezzo del prodotto personalizzato sia visualizzato nel catalogo.
1. In qualità di cliente B2B, aggiungi il prodotto al carrello.

<u>Risultato previsto</u>:

Il prezzo corretto viene visualizzato nel carrello e corrisponde al prezzo nel catalogo.

<u>Risultato effettivo</u>:

Il prezzo personalizzato scompare e viene visualizzato il prezzo regolare del catalogo predefinito.

## Applicare la patch

Per applicare singole patch, utilizzare i seguenti collegamenti, a seconda del prodotto Adobe Commerce:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili nello strumento QPT, fare riferimento alla sezione [Patch disponibili nello strumento QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
