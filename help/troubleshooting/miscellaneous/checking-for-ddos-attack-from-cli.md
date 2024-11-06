---
title: Controllo dell'attacco DDoS da CLI
description: In questo articolo viene illustrato il problema di come verificare la presenza di attacchi Distributed Denial of Service (DDoS) dall'interfaccia CLI (Command Line Interface) del server.
exl-id: dfdef289-cf51-42d7-b3fb-d4d2d3760951
feature: Observability
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 0%

---

# Controllo dell&#39;attacco DDoS da CLI

In questo articolo viene illustrato il problema di come verificare la presenza di attacchi Distributed Denial of Service (DDoS) dall&#39;interfaccia CLI (Command Line Interface) del server.

## Prodotti e versioni interessati

* Adobe Commerce, tutte le versioni
* Magento Open Source, tutte le versioni

## Problema

Il sito Web è lento e non è possibile accedere ad altri strumenti di analisi diversi da CLI per verificare la presenza di un potenziale attacco DDoS. I sintomi di un attacco DDoS possono variare notevolmente a seconda della configurazione di rete, del software utilizzato e così via.

Tuttavia, si consiglia di utilizzare prodotti software di analisi appositamente progettati per aiutare a identificare gli attacchi DDoS.

## Causa

Esistono diverse cause possibili per un sito web lento, tra cui un server a prestazioni ridotte, un utilizzo elevato della CPU o una configurazione errata negli script, nel codice o nell’hardware a basso costo. A volte può essere dovuto a un attacco DDoS. Due degli strumenti di base necessari per verificare la presenza di un attacco DDoS sono i registri di Adobe Commerce e la CLI.

Anche in questo caso è importante notare che l&#39;utilizzo di software specificamente progettato per identificare gli attacchi DDoS sarebbe molto utile nelle indagini.

## Passaggi della soluzione

1. Controlla i registri di Adobe Commerce per vedere se si verifica qualcos’altro oltre a un attacco DDoS. Per ulteriori informazioni, consulta i seguenti articoli nella documentazione per gli sviluppatori:
   * [Percorsi dei registri di Adobe Commerce e Magento Open Source](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/enable-logging)
   * [Percorsi dei registri dell&#39;infrastruttura cloud di Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations)
1. Iniziare a utilizzare CLI per controllare tutte le connessioni Internet correnti utilizzando il comando `netstat`: `netstat -na`. In questo modo vengono visualizzate tutte le connessioni stabilite attive al server. Qui potresti notare troppe connessioni provenienti dallo stesso indirizzo IP.
1. Per restringere ulteriormente i risultati delle connessioni stabilite solo a quelle che si connettono sulla porta 80 (la porta http del sito Web), in modo da poter ordinare e riconoscere troppe connessioni da un indirizzo IP o da un gruppo di indirizzi IP, utilizzare questo comando: `netstat -an | grep :80 | sort`. È possibile ripetere lo stesso comando per https sulla porta 443: `netstat -an | grep :443 | sort`. Un&#39;altra opzione consiste nell&#39;estendere il comando originale a entrambe le porte 80 e 443: `netstat -an | egrep ":80|:443" | sort`.
1. Per verificare se nel server sono presenti molti `SYNC_REC` attivi, utilizzare il comando:     `netstat -n -p|grep SYN_REC | wc -l`     Questo valore è di solito inferiore a 5, ma potrebbe essere molto più alto per un attacco DDoS, anche se per alcuni server un numero più alto potrebbe essere una condizione normale.
1. Per elencare tutti gli indirizzi IP che inviano stati `SYNC_REC`, utilizzare il comando: `netstat -n -p | grep SYN_REC | sort -u`.
1. Per elencare ulteriormente tutti gli indirizzi IP univoci che inviano stati `SYNC_REC`, utilizzare il comando: `netstat -n -p | grep SYN_REC | awk ‘{print $5}’ | awk -F: ‘{print $1}’`.
1. È inoltre possibile utilizzare il comando `netstat` per contare e calcolare il numero di connessioni effettuate da ogni indirizzo IP al server: `netstat -ntu | awk ‘{print $5}’ | cut -d: -f1 | sort | uniq -c | sort -n`.
1. Per visualizzare il numero di connessioni del protocollo UDP o TCP connesse al server, utilizzare il comando: `netstat -anp |grep ‘tcp|udp’ | awk ‘{print $5}’ | cut -d: -f1 | sort | uniq -c | sort -n`.
1. Per verificare le connessioni stabilite, anziché tutte e visualizzare il conteggio delle connessioni per ogni indirizzo IP, utilizzare il comando: `netstat -ntu | grep ESTAB | awk ‘{print $5}’ | cut -d: -f1 | sort | uniq -c | sort -nr`.
1. Per visualizzare i conteggi di connessione elencati per indirizzo IP alla porta 80, utilizzare il comando: `netstat -plan|grep :80|awk {‘print $5’}|cut -d: -f 1|sort|uniq -c|sort -nk 1`.

Assicurati di avere qualcuno che fornisca un&#39;analisi corretta dei dati trovati per determinare se stai effettivamente avendo un attacco DDoS. L&#39;utilizzo dei comandi `netstat` della CLI del server nei passaggi descritti in precedenza consente di analizzare se si verifica un attacco DDoS, ma l&#39;utilizzo di prodotti di analisi software appositamente progettati per aiutare a identificare gli attacchi DDoS, insieme all&#39;analisi corretta, sono gli strumenti migliori per identificare le minacce DDoS.

Se si scopre di essere sotto attacco DDoS, i passaggi da eseguire dipendono dalla configurazione della rete e dal modo in cui si verifica l&#39;attacco DDoS, ma l&#39;avviso generale è quello di contattare l&#39;ISP, ottenere un nuovo indirizzo IP per il server e/o consultare professionisti IT esperti nella gestione dei problemi DDoS per analizzare e consigliare la situazione specifica.

## Letture correlate nella documentazione per gli sviluppatori:

* [Protezione DDoS](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly#ddos-protection)
* [Utilizzo dei comandi CLI](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/deployment/examples/example-using-cli)
* [CLI cloud per Commerce](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli/cloud-cli-overview)
