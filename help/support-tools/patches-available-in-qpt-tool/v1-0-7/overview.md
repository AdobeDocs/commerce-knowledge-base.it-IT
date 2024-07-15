---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.0.7'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in  [!DNL Quality Patches Tool] (QPT) v1.0.7.
exl-id: 2415ca7a-4aec-4a63-9ae9-ee7b29bbc8d7
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# Panoramica di [!DNL Quality Patches Tool] (QPT) v1.0.7

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.0.7.

QPT v1.0.7 include le seguenti patch:

1. **MDVA-29148**: è stato risolto il problema che si verificava durante la creazione di un prodotto tramite una chiamata API. L&#39;attributo personalizzato del prodotto di tipo `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` (come Multiselect) non utilizza il valore predefinito se nel payload non è stato fornito alcun valore.
1. **MDVA-29389**: è stato risolto il problema relativo alla generazione di rapporti avanzati a causa del quale il processo cronico `analytics_collect_data` indica che *La porta deve essere configurata nel parametro host (come localhost:3306)*.
1. **MDVA-30594**: è stato risolto il problema che impediva il salvataggio di un ordine con più indirizzi durante l&#39;estrazione durante la configurazione di FPT.
1. **MDVA-30782**: è stato risolto il problema relativo alla visualizzazione del blocco dinamico indipendentemente dalla regola del carrello.
1. **MDVA-30815**: è stato risolto il problema relativo al numero di risultati da visualizzare nella pagina dei risultati della ricerca quando si modifica il numero di risultati.
1. **MDVA-30837**: aggiunge opzioni di configurazione per il calcolo della spedizione gratuita in modo che l&#39;utente possa configurare l&#39;importo minimo dell&#39;ordine per ottenere la spedizione gratuita in base al subtotale (o totale complessivo).
1. **MDVA-30945**: è stato risolto il problema che causava la ricezione di un messaggio di errore irreversibile durante l&#39;aggiornamento dei carrelli `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`.
1. **MDVA-30972**: è stato risolto il problema che causava la modifica dello stato dell&#39;ordine personalizzato in *Elaborazione* dopo la creazione parziale della spedizione tramite WebApi.
1. **MDVA-31007**: è stato risolto il problema che impediva la corretta visualizzazione degli attributi degli indirizzi personalizzati nella pagina dei dettagli dell&#39;ordine nell&#39;area Il mio account e nel back-end.
1. **MDVA-31021**: è stato risolto il problema relativo a problemi di prestazioni in `module-catalog-import-export/Model/Import/Product/Option.php`. Se nella tabella `catalog_product_option` sono presenti più di ~100.000 record, la convalida di un nuovo file CSV con un singolo prodotto richiede meno di 10 secondi.
1. **MDVA-31224**: migliora le prestazioni dell&#39;operazione di reindicizzazione `catalog_product_price` per i prodotti bundle.
1. **MDVA-31282**: è stato risolto il problema che causava la presenza di doppie autorizzazioni in [!DNL Paypal PayFlow Pro] in Adobe Commerce. Le doppie autorizzazioni hanno anche l&#39;effetto di aggirare i filtri antifrode [!DNL PayFlow Pro's] e raddoppiare le tariffe delle transazioni.
1. **MDVA-31343**: è stato risolto il problema relativo alla classe corpo rimossa `page-layout-category-full-width` quando è pianificata una categoria.

Utilizza il menu a sinistra per passare a una pagina patch specifica.
