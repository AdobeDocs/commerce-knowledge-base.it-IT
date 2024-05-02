---
title: '"Panoramica: [!DNL Quality Patches Tool] (QPT) v1.0.7'''
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.0.7.
exl-id: 2415ca7a-4aec-4a63-9ae9-ee7b29bbc8d7
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] Panoramica di (QPT) v1.0.7

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.0.7.

QPT v1.0.7 include le seguenti patch:

1. **MDVA-29148**: risolve il problema che si verificava durante la creazione di un prodotto tramite una chiamata API, l’attributo personalizzato del prodotto di `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` (come Multiselect) il tipo non utilizza il proprio valore predefinito se non è stato fornito alcun valore nel payload.
1. **MDVA-29389**: risolve il problema relativo alla generazione di rapporti avanzata in cui `analytics_collect_data` cronjob scrive: *La porta deve essere configurata all&#39;interno del parametro host (come localhost:3306)*.
1. **MDVA-30594**: risolve il problema che impediva il salvataggio di un ordine con più indirizzi durante l’estrazione quando FPT è configurato.
1. **MDVA-30782**: risolve il problema relativo alla visualizzazione del blocco dinamico indipendentemente dalla regola del carrello.
1. **MDVA-30815**: risolve il problema relativo al numero di risultati di ricerca da visualizzare nella pagina dei risultati della ricerca quando si modifica.
1. **MDVA-30837**: aggiunge opzioni di configurazione per il calcolo della spedizione gratuita in modo che l’utente possa configurare l’importo minimo dell’ordine per ottenere la spedizione gratuita in base al subtotale (o totale complessivo).
1. **MDVA-30945**: risolve il problema relativo alla ricezione di un messaggio di errore irreversibile durante l’aggiornamento dei carrelli `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`.
1. **MDVA-30972**: risolve il problema relativo alla modifica dello stato dell’ordine personalizzato in *Elaborazione* dopo la creazione parziale della spedizione tramite WebApi.
1. **MDVA-31007**: è stato risolto il problema che impediva la corretta visualizzazione degli attributi degli indirizzi personalizzati nella pagina dei dettagli dell’ordine nell’area Il mio account e nel backend di.
1. **MDVA-31021**: risolve il problema relativo ai problemi di prestazioni in `module-catalog-import-export/Model/Import/Product/Option.php`. Se sono presenti più di ~100.000 record in `catalog_product_option` , la convalida di un nuovo file CSV con un singolo prodotto richiede meno di 10 secondi.
1. **MDVA-31224**: migliora le prestazioni del `catalog_product_price` operazione di reindicizzazione per i prodotti bundle.
1. **MDVA-31282**: risolve il problema relativo alle doppie autorizzazioni in [!DNL Paypal PayFlow Pro] in Adobe Commerce. Le doppie autorizzazioni hanno anche l&#39;effetto di aggirare [!DNL PayFlow Pro's] filtri antifrode e raddoppiamento delle commissioni.
1. **MDVA-31343**: risolve il problema relativo alla classe body rimossa `page-layout-category-full-width` quando una categoria è pianificata.

Utilizza il menu a sinistra per passare a una pagina patch specifica.
