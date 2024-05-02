---
title: '"Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.42'''
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.42.
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

1. **ACSD-53658**: risolve il problema in cui *[!UICONTROL Recently Viewed]* i dati di prodotto non vengono aggiornati correttamente nella vista store.
1. **ACSD-54626**: risolve il problema che impediva la creazione di una nuova regola per gli ordini di acquisto (`createPurchaseOrderApprovalRule`) con `NUMBER_OF_SKUS` tramite GraphQL.
1. **ACSD-53845**: risolve il problema di timeout della connessione MySQL quando `consumer max_messages` = 0.
1. **ACSD-54890**: risolve il problema in cui `aggregate_sales_report_bestsellers_data` causa errori MySQL dovuti a `/tmp` spazio su disco insufficiente.
1. **ACSD-55112**: risolve il problema relativo alla presenza di *[!UICONTROL Submit review]* può essere cliccato più volte senza [!DNL Google reCAPTCHA v3] convalida.
1. **ACSD-54264**: corregge il problema relativo al punto in cui il messaggio di errore *Impossibile aggiornare l&#39;attributo richiesto. ID riga: store_id* viene visualizzato quando un cliente tenta di effettuare il Check-Out con un preventivo negoziabile da un&#39;altra visualizzazione del punto vendita.
1. **ACSD-54418**: risolve il problema relativo all’applicazione errata di un importo fisso di sconto a ciascun prodotto secondario del bundle a prezzo dinamico.
1. **ACSD-55238**: risolve il problema relativo al salvataggio della metadescrizione del prodotto vuota.
1. **ACSD-54966**: risolve il problema che impediva il riutilizzo di un codice coupon con un utilizzo limitato per cliente se l’ordine precedente non riusciva.
1. **ACSD-54060**: risolve il problema per cui un amministratore con restrizioni non può salvare un prodotto se è figlio di un altro prodotto assegnato a un ambito diverso.
1. **ACSD-48910**: risolve il problema relativo all’esaurimento delle scorte di un prodotto in bundle assegnato a più origini dopo la fatturazione e la spedizione di un ordine, anche se la quantità è diversa da zero.
1. **ACSD-55381**: corregge un errore interno del server durante la query `configurable_product_option_uid` e `configurable_product_option_value_uid` campi da un B2B *[!UICONTROL Requisition list]* tramite GraphQL.
1. **ACSD-55628**: è stato corretto il caricamento di un file nel modulo di registrazione della società e la sostituzione di un file per un attributo del cliente nella vetrina.

Utilizza il menu a sinistra per passare a una pagina patch specifica.
