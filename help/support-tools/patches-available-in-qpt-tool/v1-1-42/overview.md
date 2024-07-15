---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.42'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in  [!DNL Quality Patches Tool] (QPT) v1.1.42.
feature: Tools and External Services
role: Admin, Developer
exl-id: 49f7ebd6-7a5f-49da-8fac-c3c2b73b52c1
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.42

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.42.

QPT v1.1.42 include le seguenti patch:

1. **ACSD-53658**: è stato risolto il problema che impediva l&#39;aggiornamento corretto dei dati di *[!UICONTROL Recently Viewed]* nella visualizzazione archivio.
1. **ACSD-54626**: è stato risolto il problema che impediva la creazione di una nuova regola ordine fornitore (`createPurchaseOrderApprovalRule`) con l&#39;attributo `NUMBER_OF_SKUS` tramite GraphQL.
1. **ACSD-53845**: è stato corretto il problema di timeout della connessione MySQL quando `consumer max_messages` = 0.
1. **ACSD-54890**: è stato risolto il problema che causava errori MySQL in `aggregate_sales_report_bestsellers_data` a causa di spazio insufficiente sul disco `/tmp`.
1. **ACSD-55112**: è stato risolto il problema per cui è possibile fare clic più volte sul pulsante *[!UICONTROL Submit review]* senza la convalida [!DNL Google reCAPTCHA v3].
1. **ACSD-54264**: è stato risolto il problema che impediva l&#39;aggiornamento dell&#39;attributo richiesto tramite il messaggio di errore *. ID riga: store_id* viene visualizzato quando un cliente tenta di effettuare il Check-Out con un preventivo negoziabile da un&#39;altra visualizzazione archivio.
1. **ACSD-54418**: risolve il problema relativo all&#39;applicazione errata di un importo fisso di sconto a ogni prodotto figlio del bundle a prezzo dinamico.
1. **ACSD-55238**: è stato risolto il problema relativo al salvataggio della metadescrizione del prodotto vuota.
1. **ACSD-54966**: è stato risolto il problema che impediva il riutilizzo di un codice coupon con utilizzo limitato per cliente se l&#39;ordine precedente non riusciva.
1. **ACSD-54060**: è stato risolto il problema che impediva a un amministratore con restrizioni di salvare un prodotto se si trattava di un prodotto secondario di un altro prodotto assegnato a un ambito diverso.
1. **ACSD-48910**: è stato risolto il problema che causava l&#39;esaurimento delle scorte di un prodotto in bundle assegnato a più origini dopo la fatturazione e la spedizione di un ordine, anche se la quantità dell&#39;ordine era diversa da zero.
1. **ACSD-55381**: è stato corretto un errore interno del server durante la query dei campi `configurable_product_option_uid` e `configurable_product_option_value_uid` da un *[!UICONTROL Requisition list]* B2B tramite GraphQL.
1. **ACSD-55628**: è stato corretto il caricamento di un file nel modulo di registrazione della società e la sostituzione di un file per un attributo cliente nella vetrina.

Utilizza il menu a sinistra per passare a una pagina patch specifica.
