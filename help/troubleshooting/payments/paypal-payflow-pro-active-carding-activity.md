---
title: PayPal Payflow Pro attività di fatturazione attiva
description: AGGIORNATO IL 2 APRILE 2019
exl-id: 9fe73788-5b67-445a-9b0d-86489125d271
feature: Cache, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '665'
ht-degree: 0%

---

# PayPal Payflow Pro attività di fatturazione attiva

AGGIORNATO IL 2 APRILE 2019

L&#39;integrazione PayPal Payflow Pro in Adobe Commerce è oggetto di un&#39;attività di targeting attivo, in cui gli aggressori tentano centinaia di dollari di transazioni con carte di credito rubate per verificare la validità della carta.

L’attività esegue attualmente il targeting delle versioni di questa integrazione Payflow Pro incluse in Adobe Commerce 2.1.x, 2.2.x, 2.3.x per Magento Open Source e Commerce (on-premise e cloud). L&#39;attività di carding è inerente al modo in cui Payflow Pro è integrato nei carrelli.

>[!NOTE]
>
>Per risolvere questi problemi, abbiamo fornito nuovi pacchetti Composer per aggiungere Google reCAPTCHA o CAPTCHA al modulo di pagamento Payflow Pro. È consigliabile installare questi pacchetti su tutte le versioni e le edizioni di Adobe Commerce.

Il problema riguarda le seguenti versioni di Adobe Commerce:

* Adobe Commerce on-premise v2.1.x, 2.2.x, 2.3.x
* Adobe Commerce su infrastruttura cloud v2.1.x, 2.2.x, 2.3.x

## Problema

I sintomi di questi attacchi includono:

* Il tuo conto PayPal Payflow Pro mostra centinaia di transazioni fraudolente identificate
* PayPal può sospendere un conto Payflow Pro a causa di transazioni fraudolente in entrata e addebitare commissioni considerevoli

## Soluzione

Per proteggere da questi attacchi, consigliamo di aggiungere Google reCAPTCHA (consigliato) o CAPTCHA al modulo di pagamento Payflow Pro. Ciò include l’installazione dei pacchetti Composer e la configurazione di Google reCAPTCHA o CAPTCHA nell’amministrazione di Commerce.

### Pacchetti installazione

L’Adobe ha creato due opzioni di pacchetto per aggiungere Google reCAPTCHA e/o CAPTCHA al modulo di pagamento Payflow Pro. L&#39;installazione di uno di questi pacchetti aggiornerà le installazioni correnti e aggiungerà un&#39;opzione che può aiutare a migliorare questa sicurezza al modulo di pagamento Payflow Pro.

Questi pacchetti sono compatibili con le seguenti distribuzioni e versioni di Adobe Commerce:

Adobe Commerce (tutti i metodi di distribuzione) e Magento Open Source 2.1.x, 2.2.x, 2.3.x

L’installazione richiede comandi CLI per l’istanza Adobe Commerce. Può essere necessaria l’assistenza dello sviluppatore.

>[!NOTE]
>
>Si consiglia di installare e configurare Google reCAPTCHA oltre a installare eventuali aggiornamenti del modulo di pagamento Payflow Pro. Questa opzione fornisce un controllo invisibile e più opzioni di configurazione.

#### Installare Google reCAPTCHA ed estrarre gli aggiornamenti dei moduli

Il `magento/module-paypal-recaptcha` Il pacchetto contiene l&#39;integrazione con Google reCAPTCHA e gli aggiornamenti del modulo di pagamento Payflow Pro. Anche se hai installato e configurato il modulo reCAPTCHA, ti consigliamo di installare questo pacchetto.

Esegui i seguenti comandi per installarlo.

**Per Adobe Commerce on-premise:**

```bash
composer require magento/module-paypal-recaptcha
bin/magento module:enable Magento_PaypalReCaptcha
bin/magento setup:upgrade
bin/magento cache:clean
```

**Per l’infrastruttura cloud di Adobe Commerce:**

1. Esegui il comando seguente:

   ```bash
   composer require magento/module-paypal-recaptcha
   ```

1. Commit e push delle modifiche:

   ```bash
   git add -A && git commit -m "Install Google reCAPTCHA"    git push origin %branch_name%
   ```

1. Attendere il completamento della distribuzione.

#### Installare gli aggiornamenti del modulo di estrazione per CAPTCHA

Il `magento/module-paypal-captcha` Il pacchetto contiene l’integrazione con il modulo Adobe Commerce CAPTCHA nativo.

Esegui i seguenti comandi per installarlo:

**Per Adobe Commerce on-premise:**

```bash
composer require magento/module-paypal-captcha
bin/magento module:enable Magento_PaypalCaptcha
bin/magento setup:upgrade
bin/magento cache:clean
```

**Per l’infrastruttura cloud di Adobe Commerce:**

1. Esegui il comando seguente:

   ```bash
   composer require magento/module-paypal-captcha
   ```

1. Commit e push delle modifiche:

   ```bash
   git add -A && git commit -m "Install CAPTCHA"    git push origin %branch_name%
   ```

1. Attendere il completamento della distribuzione.

### Configurare Google reCAPTCHA o CAPTCHA

Dopo aver installato il pacchetto, configura Google reCAPTCHA (consigliato) o CAPTCHA come descritto nei seguenti documenti:

* [Google reCAPTCHA](https://docs.magento.com/user-guide/stores/security-google-recaptcha.html) nella guida utente.
* [CAPTCHA](https://docs.magento.com/user-guide/stores/security-captcha.html) nella guida utente.

La nuova opzione del modulo di pagamento è:

* Google reCAPTCHA: da utilizzare nel modulo di pagamento PayPal Payflow Pro
* CAPTCHA: Payflow Pro

## Supporto PayPal e contatti

Contatta l&#39;assistenza per gli esercenti PayPal Payflow per ulteriori informazioni sui servizi di protezione dalle frodi. Puoi richiedere al team di supporto PayPal di abilitare [Servizi di base per la protezione dalle frodi](https://developer.paypal.com/api/nvp-soap/payflow/fraud-protection/) I filtri consentono di esercitare il controllo più rigoroso possibile sui pagamenti, in modo da poter rifiutare automaticamente i pagamenti che probabilmente comporteranno transazioni fraudolente e accettare pagamenti che in genere non costituiscono un problema. Ricorda che, una volta attivati i filtri di PayPal Fraud Protection Services, la liquidazione delle transazioni può richiedere fino a 2 ore.

>[!NOTE]
>
>Per ulteriori informazioni, consulta la KB di PayPal [&quot;Adobe mi ha contattato in merito alla mia integrazione con Payflow Pro. Cosa devo fare?&quot;](https://www.paypal.com/us/smarthelp/article/ts2242).

**PayPal Payflow Dettagli di supporto per gli esercenti**

L’orario di lavoro del Supporto Commerciante Payflow è dal lunedì al venerdì dalle 7:00 alle 20:00 CST. È possibile contattare il supporto commerciale Payflow per assistenza dell&#39;account telefonicamente o via e-mail:

* Telefono: 1-888-883-9770 (prompt di selezione 2)
* Clienti internazionali: 1-408-967-0191
* E-mail: [payflow-support@paypal.com](mailto:payflow-support@paypal.com)

Supporto australiano

* Lunedì-venerdì 8:00 - 19:00 (ora dell&#39;UA)
* Telefono: +61 2 8288 0198
* E-mail: [gateway-ausupport@paypal.com](mailto:gateway-ausupport@paypal.com)
