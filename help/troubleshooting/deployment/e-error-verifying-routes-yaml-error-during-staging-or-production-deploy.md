---
title: "E: Errore durante la verifica dell’errore route.yaml durante la distribuzione di staging o produzione"
description: '"Questo articolo fornisce una soluzione per il problema dell’infrastruttura cloud di Adobe Commerce, in cui viene visualizzato il messaggio di errore *"E: Error while verifying route.yaml"* (Errore durante la verifica delle route.yaml) durante il tentativo di distribuire il progetto nell''ambiente di staging o di produzione."'
exl-id: 7f58591a-5581-46cd-984d-09ac2c0f3903
feature: Deploy, Routes, Staging
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 0%

---

# E: Errore durante la verifica dell’errore route.yaml durante la distribuzione di staging o produzione

Questo articolo fornisce una soluzione per il problema dell&#39;infrastruttura cloud di Adobe Commerce, in cui viene visualizzato il messaggio di errore *&quot;E: Errore durante la verifica delle route.yaml&quot;* durante il tentativo di distribuire il progetto nell&#39;ambiente di staging o produzione.

## Versioni interessate

* Adobe Commerce su infrastruttura cloud, tutte le versioni

## Problema

<u>Passaggi da riprodurre</u>:

Attiva una distribuzione inviando il codice all’ambiente di staging o produzione.

<u>Comportamento previsto</u>:

Implementazione completata.

<u>Comportamento effettivo</u>:

La distribuzione è bloccata e nel registro viene visualizzato il seguente messaggio di errore:

<pre>Distribuzione di applicazioni Verifica della configurazione E: errore durante la verifica di route.yaml.
I seguenti domini sono configurati per il cluster, ma non hanno route definite nel file route.yaml:

- store1.example.com
- store2.example.com
- test-store.example.com

Con la configurazione route.yaml corrente,
  Questi domini NON verrebbero serviti.

Per continuare, vedere qui per le istruzioni per la risoluzione dei problemi:
 /help/troubleshooting/deployment/e-error-verifying-routes-yaml-error-during-staging-or-production-deploy.md</pre>

## Causa

Questo errore si verifica se nel file `routes.yaml` manca la configurazione della route per eventuali domini aggiuntivi aggiunti al progetto.

Come parte dell&#39;aggiornamento dell&#39;abilitazione self-service di Adobe Commerce per la configurazione delle route self-service, è stato aggiunto un controllo pre-distribuzione per verificare che tutti i domini nel progetto abbiano route configurate nel file `routes.yaml`. Se in alcuni domini manca la configurazione della route, la distribuzione viene bloccata.

## Soluzione

Per risolvere la distribuzione bloccata, aggiornare il file `routes.yaml` per configurare le route per i domini elencati nel messaggio di errore utilizzando uno dei metodi seguenti:

* Applicare la patch fornita da Adobe Commerce durante il processo di aggiornamento.
* Aggiungere manualmente la configurazione di route mancante al file `routes.yaml`.

### Metodo 1: applicare la patch fornita da Adobe Commerce

1. Cerca un ticket di supporto Adobe Commerce recente con il titolo &quot;*Abilita funzioni self-service per &lt;project\_ID>&quot;.*
1. Segui le istruzioni riportate nel ticket per applicare la patch, che aggiorna la configurazione del percorso per l’ambiente cloud.
1. Сometti e invia le modifiche per ridistribuire il progetto.

### Metodo 2: aggiungere manualmente la configurazione di route mancante

1. Per gestire tutti i domini del progetto utilizzando la stessa configurazione di route, aggiornare il file `routes.yaml` aggiungendo i modelli di route per il dominio predefinito e tutti gli altri domini del progetto, come illustrato nell&#39;esempio seguente:

   ```yaml
   "http://{default}/":
       type: upstream
       upstream: "mymagento:http"
   "http://{all}/":
       type: upstream
       upstream: "mymagento:http"
   ```

1. Сometti e invia le modifiche per ridistribuire il progetto.

Per istruzioni dettagliate sull&#39;aggiornamento della configurazione della route, vedere [Cloud for Adobe Commerce > Configurare le route](https://devdocs.magento.com/guides/v2.3/cloud/project/project-conf-files_routes.html) nella documentazione per gli sviluppatori.

>[!NOTE]
>
>Se la configurazione del progetto specifica domini non più in uso, completa i passaggi seguenti per rimuoverli dal progetto non appena possibile: 1. Invia un ticket di supporto con un elenco di domini da rimuovere dagli ambienti di progetto. 2. Dopo che il team di supporto ha rimosso i domini, aggiornare il file `routes.yaml` per rimuovere eventuali riferimenti ai domini obsoleti.
