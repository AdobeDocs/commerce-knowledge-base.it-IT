---
title: Il servizio Elasticsearch non è in esecuzione
description: Questo articolo fornisce soluzioni per gli errori che possono verificarsi quando il servizio Elasticsearch (ES) non è in esecuzione (in genere a causa di un arresto anomalo). I sintomi possono includere errori durante l’esecuzione di controlli di integrità utilizzando curl, reindicizzazione utilizzando la riga di comando, errori di Eccezione e PHP ed errori nelle pagine dei prodotti. Nella tabella sono elencati gli errori e i collegamenti alle risorse per tentare di risolverli. Un sintomo può avere una serie di cause diverse.
exl-id: 2c2230de-cb30-4a03-8c3e-d9f44783dbae
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 0%

---

# Il servizio Elasticsearch non è in esecuzione

Questo articolo fornisce soluzioni per gli errori che possono verificarsi quando il servizio Elasticsearch (ES) non è in esecuzione (in genere a causa di un arresto anomalo). I sintomi possono includere errori durante l’esecuzione di controlli di integrità utilizzando curl, reindicizzazione utilizzando la riga di comando, errori di Eccezione e PHP ed errori nelle pagine dei prodotti. Nella tabella sono elencati gli errori e i collegamenti alle risorse per tentare di risolverli. Un sintomo può avere una serie di cause diverse.

## Elasticsearch di compatibilità della versione con Adobe Commerce

* Adobe Commerce on-premise e Adobe Commerce sull’infrastruttura cloud:

   * v2.2.3+ supporta ES 5.x
   * v2.2.8+ e v2.3.1+ supportano ES 6.x
   * ES v2.x e v5.x non sono consigliati a causa di [fine del ciclo di vita](https://www.elastic.co/support/eol). Tuttavia, se si dispone di Adobe Commerce v2.3.1 e si desidera utilizzare ES 2.x o ES 5.x, è necessario [Modificare il client php Elasticsearch](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/overview-search).

* Il Magento Open Source v2.3.0+ supporta ES 5.x e 6.x (ma si consiglia 6.x).

<table>
<tr>
<th>Sintomi quando il servizio ES non è in esecuzione</th>
<th>Dettagli</th>
<th>Risorse</th>
</tr>
<tr>
<td rowspan="3">Errori di eccezione</td>
</tr>
<tr>
<td>
<code>&lbrace;"0":"&lbrace;\"error\":&lbrace;\"root_cause\":[{\"type\":\"illegal_argument_exception\",\"reason\":\"Fielddata is disabled on text fields by default. Set fielddata=true on [%attribute_code%]] in order to load fielddata in memory by uninverting the inverted index. Note that this can however use significant memory.\"}&rbrack;</code>
</td>
<td>
<a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/elasticsearch-5-is-configured-but-search-page-does-not-load-with-fielddata-is-disabled...-error.html">L'Elasticsearch 5 è configurato, ma la pagina di ricerca non viene caricata con l'errore "Fielddata is disabled..."</a> nella Knowledge Base del supporto tecnico.
</td>
</tr>
<tr>
<td>
<code>Elasticsearch\Common\Exceptions\NoNodesAvailableException: Noticed exception 'Elasticsearch\Common\Exceptions\NoNodesAvailableException' with message 'No alive nodes found in your cluster' in /app/&lt;projectid&gt;/vendor/elasticsearch/elasticsearch/src/Elasticsearch/ConnectionPool/StaticNoPingConnectionPool.php:51</code>
</td>
<td>
Gli indici Elasticsuite non vengono eliminati.  Vedi <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/elasticsuite-tracking-indices-causes-problems-with-elasticsearch.html">Gli indici di tracciamento ElasticSuite causano problemi con Elasticsearch</a> nella nostra knowledge base di supporto.
 </td>
</tr>
<tr>
<td>Errore PHP</td>
<td>
<i>Nessun nodo attivo trovato nel cluster","1":"#0 /app/&lt;projectid&gt;/vendor/elasticsearch/elasticsearch/src/Elasticsearch/Transport.php</i>
</td>
<td rowspan="4">
<ul>
<li>Risorse per spazio su disco insufficiente:<ul>
<li><a href="https://www.cyberciti.biz/datacenter/linux-unix-bsd-osx-cannot-write-to-hard-disk/">8 Suggerimenti per risolvere i problemi relativi al disco rigido dei sistemi Linux e Unix, ad esempio Disco pieno o Impossibile scrivere sul disco</a></li>
<li><a href="https://serverfault.com/questions/315181/df-says-disk-is-full-but-it-is-not">serverfault: df indica che il disco è pieno, ma non</a></li>
<li><a href="https://unix.stackexchange.com/questions/125429/tracking-down-where-disk-space-has-gone-on-linux">unix.stackexchange.com: Individuazione dello spazio su disco disponibile su Linux</a></li>
<li>I file di registro non vengono archiviati con sufficiente regolarità. Consulta <a href="https://experienceleague.adobe.com/en/docs/commerce-admin/systems/action-logs/action-log-archive">Configurare l'archivio dei registri</a> nella documentazione per gli sviluppatori.</li>
<li>Le directory di sistema dei file non sono ottimizzate. Consulta <a href="https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/developer-tools#resource-file-optimization">Ottimizzazione file</a> nella documentazione per gli sviluppatori.</li>
<li>Se le soluzioni descritte nella documentazione precedente non risolvono il problema, contatta il team dell’account Adobe per richiedere ulteriore spazio di archiviazione.</li>
</ul>
</li>
<li>Se il disco non ha esaurito lo spazio di archiviazione ma si ricevono ancora i messaggi di errore nella colonna sinistra, <a href="/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket">invia un ticket di supporto</a>.</li>
</ul>
<ul>
<li>Vedi <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/elasticsuite-tracking-indices-causes-problems-with-elasticsearch.html">Gli indici di tracciamento ElasticSuite causano problemi con Elasticsearch</a> nella nostra knowledge base di supporto.
</li>
</ul>
</td>
</tr>
<tr>
<td><code>Curl</code> errore</td>
<td>L'esecuzione del comando <code>curl</code> per verificare l'integrità dell'Elasticsearch:<code>curl -m1 localhost:9200/_cluster/health?pretty</code>(o<code>curl -m1 elasticsearch.internal:9200/_cluster/health?pretty</code>per gli account Starter) genera l'errore seguente: <i>Errore: curl: (7) Impossibile connettersi alla porta localhost 9200: connessione rifiutata</i> </td>
</tr>
<tr>
<td>Errore della riga di comando</td>
<td>L'esecuzione di <code>$ bin/magento indexer:reindex catalogsearch_fulltext</code> genera l'errore <i>Errore sconosciuto del processo dell'indicizzatore di ricerca nel catalogo:
        Nessun nodo attivo trovato nel cluster</i>
</td>
</tr>
<tr>
<td>Errore nelle pagine dei prodotti
</td>
<td><i>Si è verificato un errore durante l'elaborazione della richiesta.
      La stampa dell'eccezione è disabilitata per impostazione predefinita per motivi di sicurezza</code></i>
</tr>
</table>
