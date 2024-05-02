---
title: '"Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.12'''
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.12.
exl-id: 749dbfd5-9ded-4919-8c57-0f66c85751e9
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) Panoramica della versione 1.1.12

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.12.

QPT v1.1.12 include le seguenti patch:

1. **MDVA-39546**: risolve il problema per cui la data di inizio per l’aggiornamento della gestione temporanea poteva essere impostata su una data precedente alla data corrente durante la modifica.
1. **MDVA-39713**: risolve il problema per cui l’utente può modificare l’ora di inizio di un aggiornamento pianificato attivo.
1. **MDVA-39993**: risolve il problema per cui le modifiche di inventario eseguite tramite API non si riflettono sulla pagina del prodotto sul front-end.
1. **MDVA-41136**: corregge il problema in cui la data di scadenza del `mage-cache-sessid` non viene esteso, con conseguente pulizia dei dati del cliente.
1. **MDVA-41229**: è stato corretto il problema per cui le immagini disponibili sul back-end non venivano visualizzate sul front-end dopo l’importazione di prodotti configurabili.
1. **MDVA-41628**: risolve il problema relativo all’accesso alle nuove risorse da parte degli utenti amministratori con restrizioni esistenti quando vengono aggiunti nuovi moduli.
1. **MDVA-42410**: risolve il problema relativo alla visualizzazione dei rapporti coupon solo della valuta di base predefinita.
1. **MDVA-42645**: risolve il problema per cui l’amministratore non può rimborsare i punti premio se la funzionalità di credito del negozio è disabilitata.
1. **MDVA-42689** Adobe Commerce : risolve il problema relativo alla generazione di un *Violazione del vincolo di integrità* errore durante l’aggiornamento delle categorie di prodotto durante l’importazione.
1. **MDVA-42855**: risolve il problema per cui un nuovo indirizzo del cliente non viene salvato nella rubrica durante il pagamento.
1. **MDVA-42950**: risolve il problema per cui i video non vengono riprodotti sulla pagina del prodotto.
1. **MDVA-43232**: risolve il problema relativo all’ordinamento dei prodotti in [!DNL Visual Merchandiser] In base al prezzo speciale in basso/superiore viene generato un errore durante il salvataggio della categoria.
1. **MDVA-43348**: corregge il problema per cui la richiesta GraphQL di gift card mostra un errore se `gift_card_options` contain *uid*.
1. **MDVA-43414**: corregge l’errore irreversibile PHP che si verifica durante l’esecuzione di `inventory.reservations.updateSalabilityStatus` mette in coda il consumatore negli SKU numerici.
1. **MDVA-43726**: risolve il problema per cui la regola del prezzo di catalogo basata sulla corrispondenza dell’attributo a livello di negozio non viene applicata dopo una reindicizzazione parziale.
1. **MDVA-43731**: risolve il problema in cui *Sinonimi di ricerca* non funziona più quando il valore viene aggiunto in *Condizioni minime da rispettare*.

Utilizza il menu a sinistra per passare a una pagina patch specifica.
