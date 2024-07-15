---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.34'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in  [!DNL Quality Patches Tool] (QPT) v1.1.34.
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

1. **ACSD-52277**: è stato risolto il problema che impediva il reindirizzamento corretto di un utente amministratore dopo aver selezionato la visualizzazione archivio durante la creazione di un nuovo ordine nell&#39;amministratore.
1. **ACSD-50813**: è stato risolto il problema che impediva a un amministratore di aggiungere all&#39;ordine di amministrazione prodotti in bundle contenenti una barra nello SKU con la funzionalità [!UICONTROL Add Products by SKU].
1. **ACSD-51630**: è stato risolto il problema che rallentava il download delle pagine di amministrazione a causa di una grande quantità di messaggi di sistema.
1. **ACSD-51853**: è stato corretto il problema per cui gli stili di testo copiati non vengono applicati quando si utilizza [!DNL Page Builder].
1. **ACSD-52160**: è stato risolto il problema che impediva la corretta valutazione di un risultato di convalida del prodotto in base alla regola del prezzo del carrello, in base alla condizione della regola *Se un elemento viene trovato/NON trovato nel carrello con tutte/tutte queste condizioni true*.
1. **ACSD-51636**: è stato risolto il problema che impediva a un amministratore di aggiungere nuovi utenti dalla sezione account cliente nonostante disponesse di tutti i ruoli e le autorizzazioni necessari.
1. **ACSD-51739**: è stato risolto il problema che si verificava quando veniva restituito un errore quando `structure_id` veniva richiesto in una richiesta GraphQL `CompanyTeam`.
1. **ACSD-51857**: è stato risolto il problema relativo alle prestazioni lente del report cron `aggregate_sales_report_bestsellers_data` che influisce sulle tabelle di database `sales_order` e `sales_order_item` di grandi dimensioni.
1. **ACSD-48448**: è stato risolto il problema relativo a una situazione di tipo &quot;race condition&quot; che si verificava durante l&#39;annullamento dell&#39;ordine e che causava la duplicazione delle voci nella tabella *inventory_booking*.
1. **ACSD-52689**: è stato risolto il problema che impediva il caricamento delle immagini nell&#39;archiviazione [!DNL Amazon S3] tramite l&#39;API REST.

Utilizza il menu a sinistra per passare a una pagina patch specifica.
