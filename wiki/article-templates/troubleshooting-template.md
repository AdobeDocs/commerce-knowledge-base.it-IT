---
title: '...'
labels: troubleshooting,...
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---


# Modello di articolo per la risoluzione dei problemi

Il titolo deve descrivere brevemente il problema; si preferisce un massimo di 70 caratteri.<br/>
(Esempio: &quot;Errore di memoria insufficiente durante l&#39;installazione o l&#39;aggiornamento&quot;).

Per ulteriori informazioni sui metadati, consulta [Contribuzione > Metadati](../../CONTRIBUTING.md#metadata).

Paragrafo introduttivo o due paragrafi: una breve panoramica del problema. I primi 140 caratteri sono importanti ai fini SEO (Search Engine Optimization).

## Prodotti e versioni interessati

* Adobe Commerce on-premise x.x.x
* Adobe Commerce su infrastruttura cloud x.x.x

(*In alternativa, se sono interessate le stesse versioni nel cloud o on-premise, si può dire:*)

Adobe Commerce (tutti i metodi di distribuzione) x.x.x

* Estensione o tecnologia interessata (ad es. Redis, Fastly): x.x.x

## Problema

Una descrizione chiara del problema, inclusi messaggi di errore completi come testo ed eventuali schermate importanti.
Se si trova in un registro, fornisci i dettagli: quale registro, posizione.

Rimuovi eventuali ID progetto o informazioni cliente specifici dagli errori e dai registri. Assicurati inoltre che le informazioni sensibili non siano incluse nelle schermate.

Se il problema si verifica in una situazione molto specifica, fornisci i passaggi dettagliati per riprodurre, il risultato previsto e il risultato effettivo nel formato seguente:

<u>Passaggi da riprodurre</u>:

Prerequisiti: ... (se presenti).

1. Primo passaggio.
1. Secondo passaggio.
1. ....

<u>Risultato previsto</u>:

Adobe Commerce esegue questa operazione.

<u>Risultato effettivo</u>:

Adobe Commerce lo fa.

## Causa

Il motivo per cui si verifica il problema. Non descrivere la correzione, dovrebbe essere nella sezione successiva. Ignora questa opzione se il motivo non è chiaro o non è importante in questo caso.

## Soluzione

Come risolvere il problema. Utilizzare un elenco numerato per i passaggi.
Completa la sezione con i risultati: errore non visualizzato, distribuzione funzionante, valore modificato e come visualizzare la modifica, ecc.

Se esiste una soluzione alternativa temporanea, specificala come sezione separata sotto a questa.

## Lettura correlata

* [Argomento dell&#39;articolo](https://experienceleague.adobe.com/it/docs/commerce-admin/user-guides/home) nella guida utente.
* [Argomento dell&#39;articolo](https://developer.adobe.com/commerce/docs/) nella documentazione per gli sviluppatori. Puoi anche dire di distinguere tra le istruzioni contenute nei devdocs per gli utenti cloud e quelle per gli utenti on-premise: &quot;[Argomento dell&#39;articolo](https://developer.adobe.com/commerce/docs/) nella nostra documentazione per sviluppatori per Adobe Commerce sull&#39;infrastruttura cloud.&quot; vs &quot;[Argomento dell&#39;articolo](https://developer.adobe.com/commerce/docs/) nella documentazione per gli sviluppatori di Adobe Commerce on-premise.&quot;
* [Argomento dell&#39;articolo](https://support.magento.com/hc/en-us) nella Knowledge Base di supporto.
* Qualsiasi risorsa correlata (blog, forum, StackOverflow, ecc.)
