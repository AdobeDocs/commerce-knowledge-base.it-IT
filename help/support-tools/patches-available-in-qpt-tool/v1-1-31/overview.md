---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.31'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in  [!DNL Quality Patches Tool] (QPT) v1.1.31.
exl-id: 0d93619e-0ae6-4dba-9b76-8aeb026c456d
feature: Tools and External Services
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---

# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.31

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.31.

QPT v1.1.31 include le seguenti patch:

1. **ACSD-50817**: ottimizza l&#39;esecuzione più rapida del processo cron `sales_clean_quotes` aggiungendo un indice composito nelle colonne `store_id` e `updated_at` della tabella delle virgolette.
1. **ACSD-50345**: è stato risolto il problema per cui: [!DNL Google reCAPTCHA v2] non viene ricaricato dopo l&#39;invio di un pagamento non riuscito, [!DNL Google reCAPTCHA v3 Invisible] non sta lavorando all&#39;estrazione e non è possibile effettuare l&#39;ordine e l&#39;evento [!UICONTROL PlaceOrder] non è stato attivato.
1. **ACSD-49392**: risolve il problema se lo stato dell&#39;ordine diventa chiuso dopo un rimborso parziale per un prodotto nel pacchetto.
1. **ACSD-51036**: è stato risolto il problema che causava la sovrascrittura delle informazioni sullo stato di spedizione nella tabella [!UICONTROL Items Ordered] durante le chiamate API REST simultanee.
1. **ACSD-50858**: è stato risolto il problema relativo all&#39;utilizzo errato di un coupon dopo un pagamento non riuscito con carta.

Utilizza il menu a sinistra per passare a una pagina patch specifica.
