---
title: Risolvere i problemi relativi alle prestazioni con New Relic su Adobe Commerce
description: '"Questo articolo descrive i passaggi per la risoluzione dei problemi relativi alle prestazioni dell’infrastruttura cloud di Adobe Commerce tramite New Relic. Fornisce inoltre risorse per ulteriori informazioni. Elenco dei problemi. Fai clic per visualizzare i passaggi di risoluzione dei problemi nella knowledge base di supporto:'''
exl-id: 0a22beb7-18b0-47eb-a6b8-63b7322b392c
feature: Observability
role: Developer
source-git-commit: 324cce66df1e4ab7ec4ef8fb6512c3acbabdf3ab
workflow-type: tm+mt
source-wordcount: '900'
ht-degree: 0%

---

# Risolvere i problemi relativi alle prestazioni con New Relic su Adobe Commerce

Questo articolo descrive i passaggi per la risoluzione dei problemi relativi alle prestazioni dell’infrastruttura cloud di Adobe Commerce tramite New Relic. Fornisce inoltre risorse per ulteriori informazioni. I seguenti problemi trattati nella tabella seguente con le risorse consigliate sono:

* Punteggio Apdex basso
* Utilizzo CPU elevato
* Operazioni I/O elevate
* Interruzione

<table>
<tbody>
<tr>
<td>Problema</td>
<td>Risoluzione dei problemi</td>
<td>Risorse</td>
</tr>
<tr>
<td>
<p>Punteggio Apdex basso:</p>
<p>Il tuo punteggio di <a href="https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measuring-user-satisfaction">Apdex</a> per New Relic misura la soddisfazione degli utenti per il tempo di risposta delle applicazioni e dei servizi Web.</p>
</td>
<td>
<p>Accedi a <a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; Panoramica. Sul lato destro della pagina Panoramica è visualizzato il grafico Punteggio Apdex. Un punteggio Apdex pari o inferiore a 0,5 è un punto che desta preoccupazione e merita di essere esaminato: Tempi delle transazioni web (richieste del server):</p>
<ol>
<ol>
<li>Accedi a <a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; (Seleziona un'app) &gt; Panoramica. Verificare che il filtro sia impostato su Ora transazioni Web nel filtro a discesa del grafico principale. Di seguito, nella tabella Transazioni, cerca l’ora dell’app server. Verifica se hai transazioni sospette o di lunga durata.</li>
<li>Analizzali singolarmente andando in Monitoraggio &gt; Transazioni e assicurati di impostare i filtri per Web e più dispendiosi in termini di tempo<em>.</em>
</li>
<li>Quindi cerca moduli di terze parti che consumano risorse: fornitori di pagamenti, ERP, ecc.</li>
<li>Nella sezione Monitoraggio di APM:<ol>
<li>Fare clic su Transazioni.</li>
<li>Scorri verso il basso, quindi fai clic su Mostra tabella tutte le transazioni.</li>
<li>Puoi ordinare le transazioni in base a <a href="https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems#table_view">vari parametri</a> e passare a quelli che causano sospetti.</li>
<li>Rivedi le transazioni con un punteggio Apdex basso, un conteggio insolitamente elevato o un tempo medio elevato, oppure una percentuale di Dissat.</li>
<li>Fai clic su ogni singola transazione. Se non riesci a risolvere il problema, <a href="/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket">invia un ticket di supporto.</a>
</li>
<li>Se devi approfondire l’analisi, considera la possibilità di controllare le transazioni non web.</li>
</ol>
</li>
</ol>
</ol>
<p>Tempo non di transazione Web (operazioni e attività in background):</p>
<ol>
<ol>
<li>Accedi a <a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; (Seleziona un'app) &gt; Panoramica. Accertati di selezionare l’ora delle transazioni non web nel filtro a discesa del grafico principale. Fare clic su singole transazioni nella tabella Transazioni. Cerca transazioni sospette o a lunga durata. Ciò include processi back-end, cron o processi di importazione/esportazione, inclusi processi di terze parti.</li>
</ol>
</ol>
</td>
<td>
<p>Per ulteriori informazioni sul punteggio Apdex New Relic, consulta <a href="https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction">Documentazione New Relic &gt; Apdex APM &gt; Misura la soddisfazione degli utenti</a>. È inoltre possibile fare riferimento a <a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md">Avvisi gestiti per Adobe Commerce: avviso di avviso di tipo Apdex</a> nella Knowledge Base del supporto tecnico.</p>
</td>
</tr>
<tr>
<td>
<p>Utilizzo CPU elevato:</p>
<p>Un utilizzo elevato della CPU può indicare la presenza di un servizio particolarmente occupato, come MySQL, Redis e così via.</p>
</td>
<td>
<ol>
<li>Accedi a <a href="https://login.newrelic.com/login">New Relic</a> &gt; Infrastruttura &gt; Processi.</li>
<li>Esaminare i grafici della CPU per verificare se è presente un processo bloccato o ad alto consumo che utilizza più del 100% del tempo della CPU e confrontare il numero di processori nell'istanza. Prestare attenzione ai picchi di utilizzo delle risorse. Si consiglia di non uccidere un processo a meno che non si tratti di un cron bloccato.</li>
</ol>
</td>
<td>
<p>Per ulteriori informazioni sulle metriche delle prestazioni, in particolare la percentuale della CPU, i byte di I/O e l'utilizzo della memoria per singoli processi o gruppi di processi, fare riferimento alla <a href="https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes">documentazione di New Relic &gt; pagina Interfaccia utente dell'infrastruttura &gt; pagina Host dell'infrastruttura &gt; scheda Processi</a>.</p>
</td>
</tr>
<tr>
<td>
<p>Operazioni di I/O elevate: per ogni cliente, questo numero sarebbe individuale ma significativamente diverso dalla media.</p>
</td>
<td>
<p>Individuare un picco insolito rispetto alle operazioni di I/O medie precedenti:</p>
<ol>
<li>Accedi a <a href="https://login.newrelic.com/login">New Relic</a> &gt; Infrastruttura &gt; Processi.</li>
<li>Revisione del grafico Byte di I/O letti al secondo.</li>
<li>Registra l’ora del picco.</li>
<li>Fai clic su APM.</li>
<li>Accertati di selezionare l’ora delle transazioni web nel filtro a discesa del grafico principale.</li>
<li>Imposta l’ora del picco registrato.</li>
<li>Cercare le transazioni che hanno causato operazioni di I/O elevate.</li>
<li>Eseguire un drill-down in ogni traccia di transazione &gt; Dettagli traccia per individuare la causa dei problemi.</li>
</ol>
</td>
</tr>
<tr>
<td>
<p>Interruzione: New Relic determina le interruzioni di circa Sul grafico del punteggio Apdex compare una linea rossa che indica Apdex &lt; 0,4, che è considerata un’interruzione.</p>
</td>
<td>
<p>L’analisi di un’interruzione può richiedere diversi passaggi, esaminando transazioni web e non, database e transazioni di terze parti. Transazioni Web:</p>
<ol>
<li>Accedi a <a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; Panoramica. Assicurati che il filtro sia impostato sull’ora delle transazioni web nel filtro del grafico a discesa.</li>
<li>Restringi manualmente la finestra temporale.</li>
<li>Fai clic su Transazioni. Assicurati che i filtri siano impostati su Web e più lunghi. Esaminare la transazione con la durata più lunga.</li>
<li>Se devi approfondire l’analisi, considera la possibilità di controllare le transazioni non web.</li>
</ol>
<p>Transazioni non Web:</p>
<ol>
<li>Torna alla pagina Panoramica e passa a Transazioni non web dal filtro a discesa.</li>
<li>Esamina le tracce delle transazioni in fondo alla pagina, una alla volta.</li>
<li>A seconda del problema, potrebbe essere necessario utilizzare uno strumento di terze parti come un profiler PHP per trovare un collo di bottiglia.</li>
<li>Se è necessario eseguire ulteriori indagini, è consigliabile esaminare i processi del database.</li>
</ol>
<p>Processi del database:</p>
<ol>
<li>Nella pagina APM, passare a Monitoraggio &gt; Database.</li>
<li>Ordina per la maggior parte delle operazioni che richiedono tempo.</li>
<li>Rivedi le query TOP.

Nota: <code>AGGIORNA</code> o <code>INSERISCI</code>Le query sono le query che utilizzano più la CPU.</li>
<li>Passare a Throughput dal selettore Ordina per e cercare i processi che hanno causato l'abbandono della velocità effettiva del database.</li>
<li>Se devi effettuare ulteriori indagini, prendi in considerazione la possibilità di esaminare i servizi di terze parti.</li>
</ol>
<p>Servizi di terze parti:</p>
<ol>
<li>Nella pagina APM, vai a Monitoraggio &gt; Servizi esterni.</li>
<li>Selezionare il tempo medio di risposta più lento dall'elenco a discesa Ordina per.</li>
<li>Cerca i processi che si sono verificati immediatamente prima dell’interruzione.</li>
</ol>
</td>
<td>
<p>Per ulteriori informazioni sull'analisi di problemi di prestazioni specifici, consultare <a href="https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems#tx_functions">Documentazione di New Relic &gt; Pagine dell'interfaccia utente APM &gt; Pagina Transazioni &gt; Utilizzare funzioni di espansione</a>.</p>
</td>
</tr>
</tbody>
</table>
