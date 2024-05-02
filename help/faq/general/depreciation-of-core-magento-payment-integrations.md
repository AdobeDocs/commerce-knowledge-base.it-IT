---
title: Ammortamento delle integrazioni di pagamento Adobe Commerce di base
description: A causa della direttiva sui servizi di pagamento PSD2 (consulta i dettagli sulla [direttiva sui servizi di pagamento](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/payments/compliance-payment-services-directive.html) nella nostra guida utente) e della continua evoluzione di molte API, diverse integrazioni di pagamento di base di Adobe Commerce rischiano di diventare obsolete e non più conformi alla sicurezza in futuro. A tal fine, molte integrazioni di pagamenti di base sono state o saranno presto dichiarate obsolete e si consiglia di effettuare una transizione alle corrispondenti estensioni di Commerce Marketplace. Leggi il resto dell’articolo qui sotto per rivedere le recenti dichiarazioni di obsolescenza delle integrazioni di pagamenti. Ciascuno dei collegamenti **Status** si trova nella nostra guida utente. **Le integrazioni seguenti verranno rimosse dalla versione 2.4.0 di Adobe Commerce e diventeranno obsolete dalle versioni 2.3.**
exl-id: c2c4b3b6-409d-466f-a4f3-dfe13ac7f972
feature: Compliance, Integration
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 0%

---

# Ammortamento delle integrazioni di pagamento Adobe Commerce di base

In virtù della direttiva sui servizi di pagamento PSD2 (si vedano i dettagli sui [Direttiva sui servizi di pagamento](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/payments/compliance-payment-services-directive.html) nella nostra guida utente) e la continua evoluzione di molte API, diverse integrazioni di pagamenti di base di Adobe Commerce rischiano di diventare obsolete e non più conformi alla sicurezza in futuro. A tal fine, molte integrazioni di pagamenti di base sono state o saranno presto dichiarate obsolete e si consiglia di effettuare una transizione alle corrispondenti estensioni di Commerce Marketplace. Leggi il resto dell’articolo qui sotto per rivedere le recenti dichiarazioni di obsolescenza delle integrazioni di pagamenti. Ognuno dei **Stato** I collegamenti sono disponibili nella guida utente. **Le seguenti integrazioni saranno tutte rimosse dalla versione 2.4.0 di Adobe Commerce e sono state rimosse dalle versioni 2.3.**

<table style="height: 243px;" width="712">
<tbody>
<tr>
<td style="width: 225.455px;"><strong>Integrazione metodo di pagamento</strong></td>
<td style="width: 226.364px;"><strong>Stato</strong></td>
<td style="width: 226.364px;"><strong>Consigli per Adobe Commerce 2.X</strong></td>
</tr>
<tr>
<td style="width: 225.455px;">Worldpay</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=en#recommended-solutions">Obsoleto dalla versione 2.3.5</a><br>2.4.0 - Rimozione completa</td>
<td style="width: 226.364px;">Chiedi al tuo provider di servizi di pagamento quale soluzione consiglia per soddisfare i requisiti di PSD2.</td>
</tr>
<tr>
<td style="width: 225.455px;">Authorize.net</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=en#recommended-solutions">Obsoleto dalla versione 2.3.4</a><br>2.4.0 - Rimozione completa</td>
<td style="width: 226.364px;">Utilizza il <a href="https://marketplace.magento.com/authorizenet-magento-module-authorizenet.html">estensione ufficiale</a> dalla Commerce Marketplace.</td>
</tr>
<tr>
<td style="width: 225.455px;">Authorize.net (Direct Post)</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=en#recommended-solutions">Obsoleto dalla versione 2.3.1</a><br>2.4.0 - Rimozione completa</td>
<td style="width: 226.364px;">Utilizza il <a href="https://marketplace.magento.com/authorizenet-magento-module-authorizenet.html">estensione ufficiale</a> dalla Commerce Marketplace.</td>
</tr>
<tr>
<td style="width: 225.455px;">CyberSource</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=en#recommended-solutions">Obsoleto dalla versione 2.3.3</a><br>2.4.0 - Rimozione completa</td>
<td style="width: 226.364px;">Utilizza il <a href="https://marketplace.magento.com/cybersource-global-payment-management.html">estensione ufficiale</a> dalla Commerce Marketplace.</td>
</tr>
<tr>
<td style="width: 225.455px;">eWay</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=en#recommended-solutions">Obsoleto dalla versione 2.3.3</a><br>2.4.0 - Rimozione completa</td>
<td style="width: 226.364px;">Chiedi al tuo provider di servizi di pagamento quale soluzione consiglia per soddisfare i requisiti di PSD2.</td>
</tr>
</tbody>
</table>

**Tieni presente che l’integrazione del metodo di pagamento di base PayPal non diventerà obsoleta né verrà rimossa e rimarrà supportata per tutte le versioni 2.3.x e 2.4.x.**

## Come mantenere i pagamenti sicuri in futuro

Per tutte le distribuzioni di Adobe Commerce e di Magento Open Source che utilizzano ancora integrazioni di pagamenti obsolete, segui le raccomandazioni riportate di seguito per assicurarti che i pagamenti dei clienti siano sicuri, che i pagamenti non vengano rifiutati e per prepararti all’aggiornamento ad Adobe Commerce 2.4.0:

* Installa e configura l’estensione ufficiale per il metodo di pagamento da [Commerce Marketplace](https://marketplace.magento.com/extensions/payments-security/payment-integration.html?_ga=2.108129217.2105547619.1564067043-238341041.1564067043) come indicato nella tabella precedente.
* Disabilita integrazioni pagamenti obsolete in Amministratore (set **Abilitato** opzione di configurazione su *No* ) pertanto non vengono più visualizzati nella vetrina come opzioni di pagamento. Assicurati invece che tutti i nuovi ordini vengano pagati tramite l’integrazione dell’estensione.
* Poiché la nuova integrazione di Commerci Marketplace non sarà in grado di elaborare le transazioni di pagamento effettuate utilizzando un&#39;integrazione di pagamento obsoleta, si consiglia di utilizzare entrambi i metodi di pagamento per un periodo di tempo parallelo, ma solo per il completamento di transazioni già registrate e per eventuali rimborsi. Per farlo, mantieni disabilitato il metodo di pagamento obsoleto, ma lascia compilati tutti i campi di configurazione.
