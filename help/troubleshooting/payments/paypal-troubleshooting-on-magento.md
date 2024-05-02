---
title: Risoluzione dei problemi di PayPal su Adobe Commerce
description: Questo articolo fornisce soluzioni per i problemi relativi all'elaborazione dei pagamenti tramite PayPal, in particolare la soluzione PayFlow Pro. Alcune raccomandazioni in questo articolo possono sembrare ovvie. Ti chiediamo di provare le opzioni di risoluzione dei problemi elencate in questa knowledge base e di includere tutte le informazioni nei ticket inseriti. I tecnici dell'assistenza Adobe Commerce o PayPal ti chiederanno di eseguire questi passaggi durante la diagnosi dei tuoi problemi.
exl-id: f0772515-8456-4f08-84b4-aeef44516f2a
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# Risoluzione dei problemi di PayPal su Adobe Commerce

Questo articolo fornisce soluzioni per i problemi relativi all&#39;elaborazione dei pagamenti tramite PayPal, in particolare la soluzione PayFlow Pro. Alcune raccomandazioni in questo articolo possono sembrare ovvie. Ti chiediamo di provare le opzioni di risoluzione dei problemi elencate in questa knowledge base e di includere tutte le informazioni nei ticket inseriti. I tecnici dell&#39;assistenza Adobe Commerce o PayPal ti chiederanno di eseguire questi passaggi durante la diagnosi dei tuoi problemi.

## Problemi comuni

La maggior parte dei problemi relativi ai pagamenti PayPal presenta sintomi simili: dopo aver specificato i dettagli della carta di pagamento e aver proceduto al pagamento, il pagamento non viene elaborato. Potrebbe invece essere presente un messaggio di errore, un errore di elaborazione del pagamento o persino una pagina vuota.

## Verifica credenziali, chiavi di crittografia e licenze

Possibili problemi: errori di stampa nei dettagli dell’account (nomi utente, password), account non validi, licenze scadute o non specificate, chiavi pubbliche e personali non valide e molti altri aspetti. Per individuare tali problemi, potrebbe essere necessario controllare anche le impostazioni di configurazione dei pagamenti.

## Applicare impostazioni coerenti in Adobe Commerce e PayPal

Assicurati di aver applicato le stesse impostazioni e di aver attivato le stesse funzionalità sia nelle impostazioni dell’amministratore di Commerce che in quelle dell’account PayPal.

### Esempio di problema di impostazioni

Quando si applica la soluzione PayPal Express Checkout, le transazioni basate sulle risposte AVS/CSC devono essere rifiutate in **Gestore PayPal** (Impostazioni servizio > Imposta > Opzioni di sicurezza) e in **Amministratore Commerce** ( **Negozi** > Configurazione > **Vendite** > **Metodi di pagamento** ...).
![magento_paypal_settings_2.4.1.png](assets/magento_paypal_settings_2.4.1.png)
Per ulteriori informazioni, consulta la documentazione: [PayPal](https://www.paypalobjects.com/en_US/vhelp/paypalmanager_help/setup.htm) e [Adobe Commerce](/docs/commerce-admin/stores-sales/payments/paypal/paypal-express-checkout.html) nella guida utente.

## Consenti transazioni di riferimento

Se il metodo di pagamento PayPal prevede l&#39;utilizzo di API con contratti di fatturazione e transazioni di riferimento, assicurati che siano attivati e configurati correttamente nelle impostazioni.

### Risoluzione dei problemi aggiuntivi

Vedi i seguenti articoli:

* [Richiesta rifiutata gateway PayPal - problema fattura duplicata](/help/troubleshooting/payments/paypal-gateway-rejected-request-duplicate-invoice-issue.md) nella nostra knowledge base di supporto.
* [Modifica l&#39;ID incremento per la nuova entità store](/help/how-to/general/change-increment-id-for-a-db-entity-order-invoice-credit-memo-etc-on-particular-store.md) nella nostra knowledge base di supporto.

## Contatta il supporto per raccogliere i registri di pagamento avanzato

Per risolvere problemi di pagamento complessi, il team di supporto Adobe Commerce può richiedere l’applicazione di una patch dedicata per abilitare la registrazione avanzata dei pagamenti. In questo caso, i passaggi da seguire sono i seguenti:

[Invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) con i seguenti dettagli:

* Specifica il problema con il maggior numero di dettagli possibile.
* Elencare i passaggi tentati da questo articolo, knowledge base e altre risorse. Includi tutti i risultati.
* Richiedere una patch per la registrazione avanzata dei pagamenti (numero di riferimento MDVA-4352) e istruzioni sull&#39;applicazione della patch.

Se ricevi la patch Registrazione pagamenti avanzata:

* Applichi il cerotto.
* Raccogliere i registri e allegarli al [ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
* Attendi ulteriori raccomandazioni dal team di supporto Adobe Commerce.
