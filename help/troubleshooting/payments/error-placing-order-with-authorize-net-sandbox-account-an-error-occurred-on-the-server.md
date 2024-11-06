---
title: Errore durante l'ordine con l'account Sandbox Authorize.net (si è verificato un errore sul server)
description: In questo articolo viene fornita una correzione per il messaggio di errore "*Un errore si è verificato sul server*" durante l'ordine tramite Authorize.Net Direct Post.
exl-id: 764a550a-3373-483c-843d-d8c848dcee35
feature: Compliance, Console, Customer Service, Orders, Payments
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# Errore durante l&#39;ordine con l&#39;account Sandbox Authorize.net (si è verificato un errore sul server)

In questo articolo viene fornita una correzione per il messaggio di errore &quot;*Si è verificato un errore sul server*&quot; durante l&#39;invio di un ordine tramite Authorize.Net Direct Post.

>[!WARNING]
>
>**Avviso di rimozione**
>
>A causa della direttiva sui servizi di pagamento [PSD2](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/payments/compliance-payment-services-directive) e della continua evoluzione di molte API, Authorize.Net rischia di diventare obsoleto e non più conforme alla sicurezza in futuro. Per questo motivo, è ora obsoleto. Ti consigliamo di disabilitarlo nella configurazione di Adobe Commerce e di passare alla corrispondente [estensione Commerce Marketplace](https://marketplace.magento.com/extensions.html).
>
>**Questa integrazione è stata rimossa da Adobe Commerce 2.4.0 ed è stata rimossa dalle versioni correnti di 2.3.**
>
>Per informazioni dettagliate su come effettuare una transizione sicura da integrazioni di pagamenti obsolete, consulta il nostro [DevBlog](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Magento-core-payment-integrations/ba-p/426445).

## Problema

Se si effettua un ordine utilizzando l&#39;account sandbox [Authorize.Net Direct Post](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/payments/error-placing-order-with-authorize-net-sandbox-account-an-error-occurred-on-the-server), viene visualizzato un messaggio di errore:

>>
&quot;Si è verificato un errore sul server. Provare a riordinare&quot;

## Causa 1: la modalità di test è abilitata

Non sembra ovvio, ma l&#39;impostazione della **Modalità di test** di Authorize.net deve essere impostata su **No** anche durante il test con l&#39;account Sandbox.

## Soluzione 1: disabilitare la modalità di test

1. Vai a **Negozi** > **Configurazione** > **Vendite** > **Metodi di pagamento** > **Altri metodi di pagamento** > **Authorize.net Direct Post**.
1. Impostare **Modalità test** su &quot;No&quot; (deselezionare **Usa valore di sistema**, quindi selezionare &quot;No&quot; nel menu).
1. Fai clic su **Salva configurazione**.

![authorize-net_test-mode_setting.png](/help/troubleshooting/miscellaneous/assets/authorize-net_test-mode_setting.png)

## Causa 2: URL errati

Le impostazioni Authorize.net potrebbero contenere indirizzi URL non corretti per le risorse critiche di Authorize.Net.

## Soluzione 2: fornire gli URL corretti

* **URL gateway:**   `https://test.authorize.net/gateway/transact.dll`
* **URL dettagli transazione:**   `https://apitest.authorize.net/xml/v1/request.api`
* **Riferimento API:**   `https://developer.authorize.net/api/reference/`

## In caso contrario: ottieni informazioni di debug

Se l&#39;invio di un ordine con Authorize.net non riesce e viene visualizzato un errore non informativo *&quot;Si è verificato un errore&quot;*, controllare Adobe Commerce `debug.log`.

### Transact.dll

Se `debug.log` è vuoto, controlla la risposta di **transact.dll** nella console del browser Web:

1. Apri la console.
1. Prima di effettuare un ordine, passare alla scheda **Rete** e selezionare **Mantieni registro**.    ![web-console_network_preserve-log.png](assets/web-console_network_preserve-log.png)
1. Filtra le risposte in base a **transact.dll** per visualizzare un messaggio di risposta con un possibile errore.    ![transact-dll_web-console_response.png](assets/transact-dll_web-console_response.png)
