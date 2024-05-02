---
title: Dati report servizi di pagamento ritardati
description: Questo articolo spiega perché la segnalazione dei dati in Payment Services potrebbe subire ritardi.
exl-id: 2f3249d1-be12-45bc-aa73-bef9766509ae
feature: Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# Dati report servizi di pagamento ritardati

Questo articolo spiega perché la segnalazione dei dati in Payment Services potrebbe subire ritardi.

## Prodotti e versioni interessati

* [Servizi di pagamento](https://marketplace.magento.com/magento-payment-services.html) è ora compatibile con Adobe Commerce versioni da 2.4.0 a 2.4.4.

## Problema

È possibile che i dati di reporting di Payment Services, per i report sullo stato dei pagamenti e degli ordini, non vengano sincronizzati immediatamente.

Dopo aver fatturato (acquisito) un ordine o emesso una nota di accredito per un ordine, ad esempio, lo stato dell&#39;ordine potrebbe non essere immediatamente disponibile.

<u>Passaggi da riprodurre</u>:

Prerequisiti: un ordine viene effettuato utilizzando la funzionalità di Payment Services.

1. Un ordine è [fatturato](https://docs.magento.com/user-guide/sales/invoice-create.html) (o [annullato](https://docs.magento.com/user-guide/sales/order-update.html#cancel-a-pending-order) o [rimborsato tramite nota di credito](https://docs.magento.com/user-guide/sales/credit-memos.html)) in [Amministratore](https://docs.magento.com/user-guide/stores/admin.html).
1. Passare al rapporto Stato pagamento ordine per visualizzare informazioni sull&#39;ordine.
1. Lo stato viene visualizzato come `AUTHORIZED`, che rappresenta lo stato dell&#39;ordine prima della fatturazione o di un&#39;altra azione dell&#39;ordine.

   Commerce non ha sincronizzato i dati e li ha inviati a Payment Services, pertanto il rapporto non riconosce ancora il nuovo stato dell&#39;ordine.

>[!NOTE]
>
>Questo è solo un caso d’uso comune. Ci possono essere altri casi d’uso in cui un’ [azione ordine](https://docs.magento.com/user-guide/sales/order-actions.html) si verifica e i dati non sono immediatamente disponibili nel report applicabile.

<u>Risultato previsto</u>: i dati del rapporto vengono popolati immediatamente dopo un’azione su un ordine.

<u>Risultato effettivo</u>: potrebbe verificarsi un ritardo nei dati del rapporto visibili per le azioni dell’ordine appena completate. I rapporti di pagamento possono subire un ritardo di 24-48 ore. Le relazioni sullo stato dei pagamenti degli ordini possono subire un ritardo di alcune ore.

## Causa

Esistono due fattori che influenzano questo ritardo nei dati visibili nell’amministratore:

* Con quale frequenza scegli di sincronizzare (esportare e mantenere) i dati da Commerce, tramite [configurazione in Admin](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/configure-admin.html).
* Periodo in cui PayPal pubblica i dati di reporting.

## Soluzione

Per i rapporti sullo stato dei pagamenti degli ordini:

1. Accedi a **Vendite** > **Servizi di pagamento**.
1. Clic **Stato pagamento ordine** per visualizzare la tabella rapporti sullo stato dei pagamenti degli ordini.
1. Forza la risincronizzazione facendo clic sul pulsante **forza risincronizzazione** nell’angolo in alto a destra della tabella dei rapporti.
1. Dovresti visualizzare l’ultima modifica della marca temporale aggiornata e le nuove transazioni caricate nella tabella del rapporto.

Per i report di pagamento PayPal, il risultato atteso è un ritardo di 24-48h dovuto alla dipendenza dall&#39;arco temporale di pubblicazione dei dati di PayPal.
