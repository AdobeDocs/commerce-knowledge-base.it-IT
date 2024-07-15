---
title: Risoluzione dei problemi relativi a New Relic su Adobe Commerce sull’infrastruttura cloud
description: Questo articolo fornisce risorse per la risoluzione dei problemi di New Relic su Adobe Commerce sull’infrastruttura cloud.
exl-id: ea763291-5c9b-4575-b2ee-820dbc367743
feature: Cloud, Observability, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# Risoluzione dei problemi relativi a New Relic su Adobe Commerce sull’infrastruttura cloud

Questo articolo fornisce risorse per la risoluzione dei problemi di New Relic su Adobe Commerce sull’infrastruttura cloud.

<table>
<tbody>
<tr>
<td class="wysiwyg-text-align-center"><strong>Problema</strong></td>
<td class="wysiwyg-text-align-center"><strong>Causa</strong></td>
<td class="wysiwyg-text-align-center"><strong>Risorse</strong></td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" colspan="3">Problemi di accesso</td>
</tr>
<tr>
<td>
<p><u>Impossibile visualizzare i progetti in New Relic.</u></p>
<p>Accedi a <em>New Relic</em> ma non riesci a visualizzare i progetti a cui dovresti essere autorizzato a visualizzare/accedere.</p>
</td>
<td>
<p>In questi casi, un utente amministratore deve aggiungerti al progetto.</p>
</td>
<td>
<p><a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html">Accesso ai servizi New Relic</a> nella Knowledge Base di supporto.</p>
</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" colspan="3">Problemi relativi ai dati</td>
</tr>
<tr>
<td>
<p><u>Dati mancanti dopo l'installazione.</u></p>
<p>Utilizzare l'utilità di diagnostica <a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/new-relic-diagnostics">New Relic</a> per cercare di identificare la causa. Se questo non aiuta, consulta le soluzioni specifiche per l’agente. I collegamenti agli articoli contenenti queste soluzioni si trovano nella colonna di destra.</p>
</td>
<td>
<p>I dati mancanti possono avere cause diverse. Potrebbe essere necessario:</p>
<ul>
<li>Verificare che l'agente sia installato.</li>
<li>Verifica il nome dell’app e il codice di licenza.</li>
<li>Riavvia il server web.</li>
<li>Assicurarsi che il sistema soddisfi i requisiti di compatibilità.</li>
<li>Impostazioni INI.</li>
</ul>
</td>
<td>
<ul>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#apm-agents">Documentazione di New Relic &gt; Agenti APM &gt; Dati non visualizzati</a></li>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#browser-agent">Documentazione di New Relic &gt; Browser New Relic &gt; Non visualizzare dati</a></li>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#infrastructure-agents">Documentazione di New Relic &gt; Infrastruttura New Relic &gt; Mancata visualizzazione dei dati</a></li>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#mobile-agents">Documentazione di New Relic &gt; New Relic Mobile &gt; Non visualizzare dati</a></li>
</ul>
</td>
</tr>
<tr>
<td>
<p><u>Discrepanza timestamp transazioni.</u> Potrebbe essere difficile trovare transazioni lunghe (più di 5 minuti) utilizzando l'interfaccia utente di New Relic. È inoltre possibile trovare transazioni visualizzate al di fuori dell'intervallo di tempo previsto.</p>
</td>
<td>
<p>Nell’interfaccia utente di New Relic viene visualizzata l’ora di fine della transazione, non l’ora di inizio.</p>
</td>
<td>
<p>Per calcolare l’inizio della transazione utilizzando l’interfaccia utente di New Relic, controlla la durata della transazione. Sottrae l’importo della durata dalla marca temporale (fine della transazione) fornita dall’interfaccia utente di New Relic.</p>
</td>
</tr>
<tr>
<td>
<p><u>Le query NerdGraph GraphQL <code>curl</code> che utilizzano caratteri speciali come <code>|</code> e <code>%</code> non funzionano</u>.</p>
</td>
<td>
<p>La funzionalità "copia in curl" di New Relic in NerdGraph non consente attualmente di gestire caratteri speciali come <code>|</code> e <code>%</code>.</p>
</td>
<td>
<p>Utilizza una libreria API diversa per risolvere il problema con caratteri speciali. Ad esempio, GraphQLClient Library per l’API Graphql su Python o Apache.commons per chiamate al linguaggio Java. Esaminare le librerie client in <a href="https://graphql.org/code/">GraphQL</a>.</p>
</td>
</tr>
<tr>
<td>
<p><u>Problemi relativi alla visualizzazione di grafici e dashboard.</u></p>
</td>
<td>
<p>Risolvi i grafici mancanti aggiungendo i domini New Relic all’elenco consentiti o disinstalla l’estensione del browser che causa i problemi.</p>
</td>
<td>
<p><a href="https://docs.newrelic.com/docs/apm/new-relic-apm/troubleshooting/charts-missing-or-do-not-render">Documentazione di New Relic &gt; Grafici mancanti o non renderizzati</a> </p>
</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" colspan="3">Problemi dell’agente PHP</td>
</tr>
<tr>
<td>
<p><u>L’agente PHP non mostra il conteggio di istanze corretto.</u></p>
</td>
<td>
<p>Il numero di istanze può aumentare a seconda dei processi back-end e della velocità effettiva. Le differenze tra i valori del server possono essere dovute ai processi in esecuzione su un server, ma non sull'altro.</p>
</td>
<td>
<p><a href="https://docs.newrelic.com/docs/agents/php-agent/troubleshooting/troubleshoot-php-agent-instance-count">Documentazione di New Relic &gt; Risoluzione dei problemi relativi al numero di istanze dell'agente PHP</a> </p>
</td>
</tr>
</tbody>
</table>
