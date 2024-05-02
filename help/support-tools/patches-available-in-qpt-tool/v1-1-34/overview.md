---
title: '"Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.34'''
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.34.
feature: Tools and External Services
role: Admin
exl-id: 79998832-26cb-4c11-a505-08c3382f86d4
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.34

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.34.

QPT v1.1.34 include le seguenti patch:

1. **ACSD-52277**: risolve il problema relativo a un utente amministratore che non viene reindirizzato correttamente dopo aver selezionato la vista store durante la creazione di un nuovo ordine nell’amministratore.
1. **ACSD-50813**: risolve il problema che impediva a un amministratore di aggiungere prodotti in bundle contenenti una barra nello SKU con [!UICONTROL Add Products by SKU] all&#39;ordine di amministrazione.
1. **ACSD-51630**: è stato risolto il problema che rallentava il download delle pagine di amministrazione a causa di una grande quantità di messaggi di sistema.
1. **ACSD-51853**: risolve il problema relativo alla mancata applicazione degli stili di testo copiati durante l’utilizzo di [!DNL Page Builder].
1. **ACSD-52160**: risolve il problema per cui un risultato di convalida del prodotto rispetto alla regola del prezzo del carrello non veniva valutato correttamente, in base alla condizione della regola *Se un articolo viene TROVATO/NON TROVATO nel carrello con Tutte/Qualsiasi di queste condizioni true*.
1. **ACSD-51636**: risolve il problema che impediva a un amministratore di aggiungere nuovi utenti dalla sezione account cliente nonostante disponesse di tutti i ruoli e le autorizzazioni necessari.
1. **ACSD-51739**: risolve il problema relativo alla restituzione di un errore quando il `structure_id` è richiesto in un `CompanyTeam` richiesta GraphQL.
1. **ACSD-51857**: risolve il problema relativo a prestazioni lente di `aggregate_sales_report_bestsellers_data` il report cron ha effetti di grandi dimensioni `sales_order` e `sales_order_item` tabelle di database.
1. **ACSD-48448**: risolve il problema relativo a una situazione di tipo &quot;race condition&quot; che si verifica durante l’annullamento di un ordine e causa la duplicazione delle voci nella *inventory_booking* tabella.
1. **ACSD-52689**: risolve il problema che impediva il caricamento delle immagini in [!DNL Amazon S3] archiviazione tramite API REST.

Utilizza il menu a sinistra per passare a una pagina patch specifica.
