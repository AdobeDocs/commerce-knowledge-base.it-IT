---
title: Impossibile modificare il motore di ricerca con Commerce Admin (il menu del motore di ricerca non è accessibile)
description: Questo articolo fornisce una soluzione per modificare il motore di ricerca di Adobe Commerce utilizzando l’amministratore di Commerce se il campo Motore di ricerca non viene visualizzato o se la casella di controllo Usa valore di sistema è disattivata e non accessibile.
exl-id: 5b0f728c-6a8d-446d-9553-5abc3d01e516
feature: Admin Workspace, Search, Variables
role: Developer
source-git-commit: e9f009cf4e072dcd9784693c10a4c16746af3cc5
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 0%

---

# Impossibile modificare il motore di ricerca con Commerce Admin (il menu del motore di ricerca non è accessibile)

>[!WARNING]
>
> [Il motore di ricerca del catalogo MySQL verrà rimosso in Adobe Commerce 2.4.0](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md). Prima di installare la versione 2.4.0, è necessario aver configurato e configurato l’host Elasticsearch.
> 
> Consulta:
> [Installare e configurare Elasticsearch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch).
> [Installare e configurare Opensearch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/opensearch)
> [Installare e configurare Live Search](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/install)

Questo articolo fornisce una soluzione per modificare il motore di ricerca di Adobe Commerce utilizzando l’amministratore Commerce se **Motore di ricerca** non viene visualizzato o il **Usa valore di sistema** la casella di controllo è disattivata e non accessibile.

In questo articolo:

* [Versioni interessate](#affected-versions)
* [Modificare il motore di ricerca con Commerce Admin (passaggi)](#change-search-engine-using-magento-admin-steps)
* [Problemi relativi ad Adobe Commerce on-premise](#magento-commerce-on-premise)
* [Adobe Commerce sull’infrastruttura cloud](#magento-commerce-cloud)

## Versioni interessate

* Adobe Commerce on-premise: 2.4.X
* Adobe Commerce sull’infrastruttura cloud:
   * Versione: 2.4.X
   * Architettura del piano Starter e Pro
* MySQL, Elasticsearch, Opensearch, Live Search: tutte le versioni supportate

## Modificare il motore di ricerca tramite Admin (passaggi)

1. Accedi all’amministratore come amministratore.
1. Nella barra laterale di amministrazione a sinistra, fai clic su **Negozi**. Quindi, sotto **Impostazioni**, scegli **Configurazione**.
1. Nel pannello a sinistra sotto **Catalogo,** scegli **Catalogo**.
1. Espandi **Ricerca nel catalogo** sezione.    ![catalog_menu.png](assets/catalog_menu.png)
1. Vai a **Motore di ricerca** e rimuovere la selezione dal **Usa valore di sistema** casella di controllo.
1. Fai clic su **Motore di ricerca** e selezionare una delle opzioni disponibili.    ![search_engine_menu.png](assets/search_engine_menu.png)
1. Clic **Salva configurazione** nell’angolo superiore destro della pagina.

## Problemi relativi ad Adobe Commerce on-premise

### Problema 1: il campo Motore di ricerca non viene visualizzato

Quando accedi a **Ricerca nel catalogo** sezione, il **Motore di ricerca** non viene visualizzato.

![search_engine_not_viewed.png](assets/search_engine_not_displayed.png)

### Causa: la vista archivio non è una configurazione predefinita

La vista Store per l’amministratore è stata impostata su un valore diverso da *Configurazione predefinita*.

Il motore di ricerca è una configurazione globale impostata a livello di applicazione, non nell&#39;ambito dell&#39;archivio. Gli archivi all’interno di un’applicazione Adobe Commerce non possono utilizzare motori di ricerca diversi.

### Soluzione: impostare la visualizzazione archivio su Configurazione predefinita

1. Accedi all’amministratore come amministratore.
1. Nella barra laterale di amministrazione a sinistra, fai clic su **Negozi**. Quindi, sotto **Impostazioni**, scegli **Configurazione**.
1. Nell&#39;angolo superiore sinistro fare clic sul pulsante **Visualizzazione store** e scegli *Configurazione predefinita*.
1. Clic **OK** nella finestra di dialogo di conferma per approvare la modifica della visualizzazione archivio.

![change_store_view.png](assets/change_store_view.png)

**Documentazione correlata:** [Modifica dell&#39;ambito](https://experienceleague.adobe.com/docs/commerce-admin/config/scope-change.html#set-the-scope) nella guida utente.

### Problema 2: impossibile deselezionare &quot;Usa valore di sistema&quot;

Quando accedi a **Ricerca nel catalogo** sezione dell’amministratore, il **Usa valore di sistema** La casella di controllo è disattivata, pertanto non è possibile rimuovere la selezione dalla casella di controllo per cambiare successivamente il motore di ricerca.

### Causa

Il motore di ricerca predefinito è stato configurato a livello di configurazione dell’applicazione in `app/etc/env.php` o `app/etc/config.php` e quindi non possono essere modificati utilizzando l’Admin.

Esempio della sezione con configurazione predefinita del motore di ricerca:

```php
'system'=>
array (
'default'=>
array (
'catalog'=>
array (
'search'=>
array (
'engine'=>'mysql',
),
),
),
),
```

### Soluzione

Rimuovi la sezione con la configurazione predefinita del motore di ricerca dalla sezione `app/etc/env.php` o `app/etc/config.php` file di configurazione.

### Articoli correlati nella documentazione per sviluppatori

[File di configurazione di Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/files/deployment-files.html) nella Guida alla configurazione di Adobe Commerce

## Adobe Commerce sull’infrastruttura cloud

Il passaggio da un motore di ricerca all’altro utilizzando l’amministratore non è disponibile in Adobe Commerce sull’infrastruttura cloud a causa del modo in cui questa è stata organizzata.

Durante il processo di distribuzione, gli script di distribuzione dell’infrastruttura cloud di Adobe Commerce verificano se l’Elasticsearch è stato dichiarato in `MAGENTO_CLOUD_RELATIONSHIPS` variabile. Se dichiarato, l&#39;Elasticsearch viene selezionato come motore di ricerca attivo e configurato automaticamente. [Motore di ricerca MySQL](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md) diventa inaccessibile in Admin. Se la relazione Elasticsearch non è stata dichiarata, MySQL è impostato su attivo e Elasticsearch diventa inaccessibile.

Si sconsiglia di modificare il `app/etc/env.php` o `app/etc/config.php` i file di configurazione direttamente nell’ambiente cloud; per questo motivo, la modifica di questi file per rendere visibile il motore di Elasticsearch nell’amministratore (la soluzione consigliata nella sezione precedente) non è applicabile al progetto cloud.

### Modificare il motore di ricerca negli ambienti di staging e produzione

Prima di passare dal motore di ricerca di MySQL a quello di Elasticsearch negli ambienti di staging e produzione, accertarsi di aver [ha inviato un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) la richiesta di abilitare l’Elasticsearch nell’ambiente e nel ticket è stata risolta correttamente.

Per modificare il motore di ricerca utilizzato negli ambienti di staging e produzione, modifica la `SEARCH_CONFIGURATION` nella tua `.magento.env.yaml` nell’ambiente locale, quindi invia le modifiche agli ambienti di integrazione e staging/produzione per renderle effettive.

Se passi all&#39;Elasticsearch 7, la variabile SEARCH\_CONFIGURATION nel `.magento.env.yaml` potrebbe presentarsi come segue:

```yaml
stage:
  deploy:
   SEARCH_CONFIGURATION:
     engine: elasticsearch7
     elasticsearch_server_hostname: hostname
     elasticsearch_server_port: '12345'
     elasticsearch_index_prefix: magento
     elasticsearch_server_timeout: '15'
```

Se stai passando a [Opensearch (in 2.4.6 e versioni successive)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/search-engine-shown-elasticsearch-despite-open-search) la variabile SEARCH\_CONFIGURATION nel risultato `.magento.env.yaml` potrebbe presentarsi come segue:

```yaml
stage:
  deploy:
   SEARCH_CONFIGURATION:
     engine: opensearch
     elasticsearch_server_hostname: hostname
     elasticsearch_server_port: '12345'
     elasticsearch_index_prefix: magento
     elasticsearch_server_timeout: '15'
```

Se sei [passaggio a Live Search](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/error-opensearch-search-engine-doesnt-exist-falling-back-to-livesearch), la variabile SEARCH\_CONFIGURATION nel risultato `.magento.env.yaml` potrebbe presentarsi come segue:

```yaml
stage:
  deploy:
   SEARCH_CONFIGURATION:
     engine: livesearch
```

### Documentazione correlata

#### Knowledge Base di supporto

* [Abilita Elasticsearch su cloud](/help/how-to/general/enable-elasticsearch-on-cloud.md)

#### Documentazione per gli sviluppatori

* [Configura servizio Elasticsearch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch.html)
* [Generare e distribuire](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) (documentazione sulla funzione `.magento.env.yaml` file di configurazione)
* [Distribuire le variabili](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html) ([SEZIONE SEARCH\_CONFIGURATION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#search_configuration))
* [Servizi](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) (documentazione sulla funzione `.magento/services.yaml` file di configurazione)
* [Live Search](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/overview)
