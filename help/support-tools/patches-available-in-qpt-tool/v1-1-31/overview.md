---
title: '"Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.31'''
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.31.
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

1. **ACSD-50817**: ottimizza il processo cron `sales_clean_quotes` per velocizzare l&#39;esecuzione aggiungendo un indice composito `store_id` e `updated_at` nella tabella delle offerte.
1. **ACSD-50345**: risolve il problema in cui: [!DNL Google reCAPTCHA v2] non si ricarica dopo l’invio di un pagamento non riuscito, [!DNL Google reCAPTCHA v3 Invisible] non funziona al momento del pagamento e l’ordine non può essere inoltrato, e [!UICONTROL PlaceOrder] evento non attivato.
1. **ACSD-49392**: risolve il problema relativo alla chiusura dello stato dell’ordine dopo un rimborso parziale per un prodotto nel pacchetto.
1. **ACSD-51036**: è stato corretto il problema per cui le race condition durante le chiamate REST API simultanee determinano la sovrascrittura delle informazioni sullo stato della spedizione in [!UICONTROL Items Ordered] tabella.
1. **ACSD-50858**: risolve il problema relativo all’utilizzo errato di un coupon dopo un pagamento non riuscito con carta.

Utilizza il menu a sinistra per passare a una pagina patch specifica.
