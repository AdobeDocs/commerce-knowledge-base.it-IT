---
title: Il motore di ricerca del catalogo MySQL verrà rimosso in Adobe Commerce 2.4.0
description: Adobe Commerce on-premise, Adobe Commerce on cloud infrastructure e Magento Open Source 2.4.0 verranno rilasciati nei prossimi mesi. Per Adobe Commerce on-premise e Magento Open Source versione 2.4.0 Elasticsearch 6.x o 7.x sarà un componente obbligatorio e il motore di ricerca MySQL verrà rimosso. In Adobe Commerce sull’infrastruttura cloud, Elasticsearch è già richiesto.
exl-id: 717be515-3cbf-42e9-9b72-caf11b8c3771
feature: Catalog Management, Search, Services
role: Admin
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 0%

---

# Il motore di ricerca del catalogo MySQL verrà rimosso in Adobe Commerce 2.4.0

Adobe Commerce on-premise, Adobe Commerce on cloud infrastructure e Magento Open Source 2.4.0 verranno rilasciati nei prossimi mesi. Per Adobe Commerce on-premise e Magento Open Source versione 2.4.0 Elasticsearch 6.x o 7.x sarà un componente obbligatorio e il motore di ricerca MySQL verrà rimosso. In Adobe Commerce sull’infrastruttura cloud, Elasticsearch è già richiesto.

>[!WARNING]
>
>Se non si installa/configura Elasticsearch 6/7 prima di tentare l’aggiornamento, potrebbero verificarsi gravi problemi con Adobe Commerce. Gli aggiornamenti del servizio su Adobe Commerce su infrastrutture cloud non possono essere inviati all’ambiente di produzione senza un preavviso di 48 ore lavorative al nostro team di infrastruttura. Ciò è necessario in quanto è necessario disporre di un tecnico del supporto dell&#39;infrastruttura per aggiornare la configurazione entro l&#39;intervallo di tempo desiderato, riducendo al minimo i tempi di inattività dell&#39;ambiente di produzione. Quindi, 48 ore prima del momento in cui le modifiche devono essere in produzione [invia un ticket di supporto](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) specificando l&#39;aggiornamento del servizio richiesto e indicando l&#39;ora in cui desideri avviare il processo di aggiornamento.

Il motivo della rimozione del motore di ricerca MySQL è dovuto al fatto che Elasticsearch fornisce funzionalità di ricerca superiori e ottimizzazioni delle prestazioni del catalogo.

## Prodotti e versioni interessati:

* Adobe Commerce on-premise v2.4.0
* Magento Open Source v2.4.0

## Aggiornamento:

<table style="height: 164px; width: 632.2px;">
<tbody>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;"><strong>Motore di ricerca</strong></td>
<td class="wysiwyg-text-align-center" style="width: 478.2px;"><strong>Azione</strong></td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">MySQL</td>
<td style="width: 478.2px;">È necessario installare Elasticsearch. Consulta <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/overview-search">Installare e configurare Elasticsearch</a> nella documentazione per gli sviluppatori.</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">Elasticsearch (senza versione elencata)</td>
<td style="width: 478.2px;">Stai utilizzando Elasticsearch 2 e devi eseguire l’aggiornamento ad Elasticsearch 7 (preferito) o 6. Per informazioni dettagliate, consulta <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/overview-search#es-upgrade6">Aggiornamento di Elasticsearch</a> e <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/configure-search-engine">Configurazione di Commerce per l'utilizzo di Elasticsearch</a> nella documentazione per gli sviluppatori.</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">ELASTICSEARCH 5</td>
<td style="width: 478.2px;">Elasticsearch 5 ha raggiunto la <a href="https://www.elastic.co/support/eol">fine del ciclo di vita</a> ed è stato dichiarato obsoleto in Adobe Commerce 2.4.0. Aggiornamento ad Elasticsearch 7 (preferito) o 6.</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">ELASTICSEARCH 6 o 7</td>
<td style="width: 478.2px;">Non è necessario eseguire alcun passaggio aggiuntivo prima dell’aggiornamento ad Adobe Commerce 2.4.0.</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">Estensione di terze parti</td>
<td style="width: 478.2px;">Non è necessario installare Elasticsearch. Adobe Commerce consiglia di contattare il fornitore del motore di ricerca per determinare se l’estensione è completamente compatibile con Adobe Commerce 2.4.0.</td>
</tr>
</tbody>
</table>

## Installazione:

Quando Adobe Commerce on-premise e Magento Open Source 2.4.0 vengono rilasciati, Elasticsearch sarà un componente richiesto, quindi devi avere un host Elasticsearch configurato e configurato prima di installare la versione 2.4.0. Consulta [Installare e configurare Elasticsearch](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/overview-search) nella documentazione per gli sviluppatori.

Per impostazione predefinita, la ricerca di Adobe Commerce utilizzerà Elasticsearch 7 come motore di ricerca e tenterà di connettersi a un server in localhost:9200. È supportato anche Elasticsearch 6.x. Se la configurazione non corrisponde ai valori predefiniti, è possibile configurare queste impostazioni utilizzando gli argomenti passati a `setup:install`, nello stesso modo in cui viene configurata la connessione al database.

Ad esempio: `setup:install --elasticsearch-host=es.mystore.com`

Durante l’installazione verrà verificata la connessione ad Elasticsearch e l’installazione avrà esito negativo se Adobe Commerce non è in grado di connettersi a un host Elasticsearch. In questo caso, verifica che l’Elasticsearch sia funzionante e che siano stati forniti i parametri di connessione corretti.
