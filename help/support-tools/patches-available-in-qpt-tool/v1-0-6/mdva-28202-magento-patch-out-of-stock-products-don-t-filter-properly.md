---
title: "Patch MDVA-28202: i prodotti esauriti non filtrano correttamente"
description: La patch MDVA-28202 risolve il problema se i prodotti esauriti non vengono filtrati correttamente utilizzando il filtro **Price** su un front-end store di Adobe Commerce. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.6.
exl-id: 45976602-15f3-4fef-9d90-da2b3fe6046d
feature: Catalog Management, Categories, Orders, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# Patch MDVA-28202: i prodotti esauriti non filtrano correttamente

La patch MDVA-28202 risolve il problema per cui i prodotti esauriti non vengono filtrati correttamente utilizzando il filtro **Prezzo** in un negozio Adobe Commerce front-end. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.6.

## Prodotti e versioni interessati

* La patch è stata progettata per Adobe Commerce su infrastruttura cloud 2.3.5-p1.
* La patch è compatibile anche con Adobe Commerce on-premise e Adobe Commerce on cloud infrastructure 2.3.4 - 2.4.1.

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I prodotti esauriti non vengono filtrati correttamente utilizzando il filtro **Prezzo** in Commerce Admin.

<u>Prerequisito:</u>

* Impostare **Visualizza prodotti esauriti** = &quot;*Sì*&quot; in **Archivi > Configurazione > CATALOGO > Inventario > Opzioni scorte**.

<u>Passaggi da riprodurre:</u>

1. Crea un prodotto configurabile con due prodotti semplici (esempio: set **Price** = *$1500*).
1. Entrambi i prodotti semplici dovrebbero essere &quot;esauriti&quot; durante la creazione del prodotto configurabile.
1. Assegna il prodotto configurabile a una categoria.
1. Reindicizza e controlla la tabella `catalog_product_index_price` utilizzando l&#39;ID entità del prodotto configurabile sopra.
1. Salvare tutti i prezzi dei prodotti = *$0*.
1. Carica la categoria e conferma la disponibilità del prodotto.
1. Apri il filtro **Prezzo** dalla navigazione su più livelli.
1. Il filtro **Prezzo** include un&#39;opzione &quot; *$0,00 - $9.99* &quot;.
1. Fai clic su questa opzione di filtro **Prezzo** e imposta il **Prezzo** = *$1500*. Otterrai il prodotto configurabile creato in precedenza.

<u>Risultato previsto:</u>

Il prodotto filtra nella fascia di prezzo corretta come previsto.

<u>Risultato effettivo:</u>

Il prodotto rientra in un filtro di fascia di prezzo errato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti riportati di seguito, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Applicare le patch utilizzando lo strumento Quality Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento Quality Patches: è stato introdotto un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Per informazioni sulle altre patch disponibili nello strumento QPT, fare riferimento alla sezione [Patch disponibili nello strumento QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).

Per ulteriori informazioni sui prodotti configurabili, consulta questo articolo nella documentazione per gli sviluppatori: [Crea un&#39;esercitazione sul prodotto configurabile](https://devdocs.magento.com/guides/v2.4/rest/tutorials/configurable-product/config-product-intro.html) nella documentazione per gli sviluppatori.
