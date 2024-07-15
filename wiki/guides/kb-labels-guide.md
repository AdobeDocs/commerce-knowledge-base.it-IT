---
source-git-commit: 88a2b8fe11d718f33c26bbc6f407c55d9f1fd189
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---
# Guida delle etichette KB

Questo documento fornisce le linee guida per l’aggiunta di etichette agli articoli nella Knowledge Base di supporto Adobe Commerce.
Le etichette (dette anche tag) migliorano l&#39;esperienza di ricerca nella [Knowledge Base del supporto Adobe Commerce](https://support.magento.com/hc/en-us).
Le etichette vengono aggiunte nel campo &quot;etichette&quot; nella sezione dei metadati di un file di articolo, separate da virgole, senza spazio tra una virgola e l’etichetta successiva.
Per informazioni dettagliate, vedere [../../.github/CONTRIBUTING.md#metadata].

## Disposizioni generali

Per ogni articolo aggiungi i seguenti tipi di etichetta:

* Etichette per prodotti. (obbligatorio)
* Etichette per le versioni interessate. (obbligatorio, tranne gli articoli di supporto generale)
* Etichetta per il tipo di contenuto. (obbligatorio)
* Etichette per i principali componenti tecnici.(se applicabile)
* Etichette per processi/funzionalità in fase di risoluzione dei problemi/descrizione. (se applicabile)
* Correzione/descrizione delle etichette per il problema. (se applicabile)

Consulta le sezioni seguenti per raccomandazioni dettagliate su come definire le etichette per ciascuno di questi tipi di etichette.

## Etichette per i prodotti

<table>
<tbody>
  <tr>
    <th>Nome del prodotto</th>
    <th>Etichetta</th>
  </tr>
  <tr>
    <td>Adobe Commerce (tutti i metodi di distribuzione) </td>
    <td>
    "Adobe Commerce, infrastruttura cloud, on-premise"
    </td>
  </tr>
  <tr>
    <td>Adobe Commerce sull’infrastruttura cloud</td>
    <td>
      "Adobe Commerce, infrastruttura cloud"
    </td>
  </tr>
  <tr>
    <td>Adobe Commerce on-premise</td>
    <td>"Adobe Commerce, on-premise"</td>
  </tr>
  <tr>
    <td>Magento Business Intelligence (MBI)</td>
    <td>
        "Magento Business Intelligence,MBI"
    </td>
  </tr>
   <tr>
    <td>Magento Open Source</td>
    <td>
        "Magento Open Source"
    </td>
  </tr>
  <tr>
    <td>B2B per Adobe Commerce</td>
    <td>"B2B"</td>
  </tr>
  <tr>
    <td>PWA per Adobe Commerce</td>
    <td>"PWA"</td>
  </tr>
  <tr>
    <td>Progetto Venia storefront</td>
    <td>Venia</td>
  </tr>
  <tr>
    <td>Strumento Patch di qualità, QPT</td>
    <td>"Strumento Patch di qualità, patch QPT"</td>
  </tr>
  </tbody>
</table>

## Etichette per le versioni dei prodotti

* Aggiungi un’etichetta separata per ogni versione di Adobe Commerce. Esempio: &quot;2.3.7&quot;
* Non aggiungere etichette per gli intervalli.
Cioè, se interessati da 2.3.0-2.3.5, aggiungere: &quot;2.3.0,2.3.1,2.3.2,2.3.2-p2,2.3.3,2.3.3-p1,2.3.4,2.3.4-p2,2.3.5-p1,2.3.5-p2&quot;
NON &quot;2.3.0-2.3.5&quot;
* Non aggiungere etichette con .x. Esempio: &quot;2.3.x&quot;

## Etichette per il tipo di contenuto (in base alla categoria)

<table>
  <tbody>
    <tr>
      <th>Categoria</th>
      <th>Etichetta</th>
    </tr>
    <tr>
      <td>Best practice</td>
      <td>"best practice" (non "best practice" né "best practice")</td>
    </tr>
    <tr>
      <td>
        Risoluzione dei problemi
      </td>
      <td>
      "risoluzione dei problemi"
      </td>
    </tr>
    <tr>
      <td>Procedura</td>
      <td>"come"</td>
    </tr>
    <tr>
      <td>Domande frequenti</td>
      <td >"FAQ"</td>
    </tr>
  </tbody>
</table>

## Etichette per i principali componenti tecnici

* Utilizzare l&#39;iniziale maiuscola in base alla denominazione ufficiale del componente.
* Non utilizzare sinonimi, un’etichetta per un componente.
* È preferibile utilizzare etichette di una parola, ma se il nome del componente contiene più parole, utilizzare più parole. Non aggiungere descrizioni dei problemi. Vale a dire, mettete &quot;Elasticsearch&quot; invece di &quot;problemi Elasticsearch&quot;.
* Se il contenuto è pertinente solo per una particolare versione del componente, aggiungi un’etichetta contenente nome + versione.\
  Esempio: &quot;Elasticsearch 5&quot;. Se è pertinente per diverse versioni particolari, aggiungi diverse etichette di questo tipo. Esempio: &quot;Elasticsearch 5&quot;, &quot;Elasticsearch 6&quot;. Se necessario, utilizzare &quot;x&quot; per più versioni. Esempio: &quot;Elasticsearch 2.x&quot;

Esempi:

* &quot;Elasticsearch&quot;
* &quot;New Relic&quot;
* &quot;Installazione guidata Web&quot;

## Etichette per processo/funzionalità in fase di risoluzione dei problemi/descrizione

* Usa maiuscole/minuscole, ad eccezione dei sostantivi corretti.
* Non utilizzare sinonimi, un’etichetta per un’entità.
* È preferibile utilizzare etichette di una parola. Non aggiungere la descrizione del problema. Ovvero, inserisci &quot;database&quot; invece di &quot;arresti anomali del database&quot;.

Esempi: 

* &quot;database&quot;
* &quot;cron&quot;
* &quot;distribuzione&quot;
* &quot;aggiornamento di massa&quot;

## Etichette per il problema da correggere/descrivere

* Usa lettere minuscole, ad eccezione dei sostantivi corretti.
* Non utilizzare sinonimi, un’etichetta per un’entità.
* È preferibile utilizzare etichette di una parola. Non convertire un messaggio di errore in etichetta.

Esempi:

* &quot;site down&quot;
* &quot;Errore 500&quot;
* &quot;cron bloccato&quot;
