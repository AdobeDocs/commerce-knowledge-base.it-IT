---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.12'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in  [!DNL Quality Patches Tool] (QPT) v1.1.12.
exl-id: 749dbfd5-9ded-4919-8c57-0f66c85751e9
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# Panoramica di [!DNL Quality Patches Tool] (QPT) v1.1.12

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.12.

QPT v1.1.12 include le seguenti patch:

1. **MDVA-39546**: è stato risolto il problema per cui la data di inizio per l&#39;aggiornamento dello staging poteva essere impostata su una data precedente a quella corrente durante la modifica.
1. **MDVA-39713**: è stato risolto il problema che impediva all&#39;utente di modificare l&#39;ora di inizio per un aggiornamento pianificato attivo.
1. **MDVA-39993**: risolve il problema per cui le modifiche di inventario eseguite tramite API non vengono applicate alla pagina del prodotto nel front-end.
1. **MDVA-41136**: è stato risolto il problema che impediva l&#39;estensione della data di scadenza di `mage-cache-sessid`, causando la pulizia dei dati del cliente.
1. **MDVA-41229**: è stato risolto il problema che impediva la visualizzazione delle immagini disponibili nel back-end dopo l&#39;importazione di prodotti configurabili.
1. **MDVA-41628**: è stato risolto il problema che impediva agli utenti amministratori con restrizioni esistenti di accedere alle nuove risorse all&#39;aggiunta di nuovi moduli.
1. **MDVA-42410**: è stato risolto il problema che causava la visualizzazione della sola valuta di base predefinita nei report coupon.
1. **MDVA-42645**: è stato risolto il problema che impediva all&#39;amministratore di rimborsare i punti premio se la funzionalità di credito dell&#39;archivio è disabilitata.
1. **MDVA-42689**: è stato corretto il problema a causa del quale Adobe Commerce generava un errore *Violazione del vincolo di integrità* durante l&#39;aggiornamento delle categorie di prodotti durante l&#39;importazione.
1. **MDVA-42855**: è stato risolto il problema che impediva il salvataggio di un nuovo indirizzo del cliente nella rubrica durante l&#39;estrazione.
1. **MDVA-42950**: è stato risolto il problema che impediva la riproduzione dei video nella pagina del prodotto.
1. **MDVA-43232**: è stato risolto il problema che causava un errore durante il salvataggio della categoria durante l&#39;ordinamento dei prodotti in [!DNL Visual Merchandiser] in base al prezzo speciale nella parte inferiore/superiore.
1. **MDVA-43348**: è stato risolto il problema che causava la visualizzazione di un errore nella richiesta GraphQL di gift card se `gift_card_options` conteneva *uid*.
1. **MDVA-43414**: corregge l&#39;errore irreversibile PHP che si verifica durante l&#39;esecuzione del consumer di coda `inventory.reservations.updateSalabilityStatus` negli SKU numerici.
1. **MDVA-43726**: è stato risolto il problema che impediva l&#39;applicazione della regola del prezzo del catalogo basata sulla corrispondenza degli attributi a livello di archivio dopo la reindicizzazione parziale.
1. **MDVA-43731**: è stato risolto il problema che impediva il funzionamento di *Sinonimi di ricerca* quando il valore viene aggiunto in *Termini minimi da abbinare*.

Utilizza il menu a sinistra per passare a una pagina patch specifica.
