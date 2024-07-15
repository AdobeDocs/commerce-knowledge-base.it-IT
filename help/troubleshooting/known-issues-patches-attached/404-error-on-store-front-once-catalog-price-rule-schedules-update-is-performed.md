---
title: 404 Errore nel negozio front una volta eseguito l'aggiornamento dei programmi di regole prezzi catalogo
description: Questo articolo fornisce una patch e i passaggi necessari per risolvere il problema noto di Adobe Commerce 2.2.1 relativo all’errore 404 su tutte le prime pagine del negozio, dopo la creazione di un aggiornamento della regola del prezzo di catalogo e la modifica del suo orario di inizio in un secondo momento. Per risolvere il problema è necessario applicare la patch.
exl-id: 7ea148a5-56cb-479a-8b2f-fae8b3bd4b22
feature: Cache, Catalog Management, Marketing Tools, Orders, Price Rules
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 0%

---

# 404 Errore nel negozio front una volta eseguito l&#39;aggiornamento dei programmi di regole prezzi catalogo

Questo articolo fornisce una patch e i passaggi necessari per risolvere il problema noto di Adobe Commerce 2.2.1 relativo all’errore 404 su tutte le prime pagine del negozio, dopo la creazione di un aggiornamento della regola del prezzo di catalogo e la modifica del suo orario di inizio in un secondo momento. Per risolvere il problema è necessario applicare la patch.

## Problema

Le pagine di vetrina non sono più disponibili, restituendo l’errore 404. Il problema viene visualizzato dopo la scadenza dell’aggiornamento attivo della regola del prezzo del catalogo, purché la data di inizio di questo aggiornamento sia stata modificata dopo la creazione iniziale.

<u>Passaggi da riprodurre</u>:

1. Nell&#39;amministratore di Commerce, crea una nuova regola di prezzo catalogo in **Marketing** > **Promozioni** > **Regola prezzo catalogo**.
1. Nella griglia **Regola prezzo catalogo**, fai clic su **Modifica,** pianifica un nuovo aggiornamento e imposta **Stato** su *Attivo.*
1. Passa a **Contenuto** > **Gestione temporanea dei contenuti** > **Dashboard.**
1. Seleziona l’aggiornamento creato di recente e modificane l’ora di inizio.
1. Salva le modifiche.

<u>Risultato previsto</u>:

Quando la data di inizio Aggiornamento diventa effettiva, la regola del prezzo di catalogo viene applicata correttamente.

<u>Risultato effettivo</u>:

Quando la data di inizio Aggiornamento diventa effettiva, tutti i cataloghi e i prodotti nella vetrina non sono più disponibili e viene restituito l’errore 404.

## Soluzione

Per ripristinare le pagine del catalogo e poter utilizzare completamente la funzionalità di aggiornamento delle regole del prezzo del catalogo, è necessario installare la patch, eliminare la regola sia manualmente che nell’amministratore e correggere i collegamenti non validi nel database. Sarà inoltre necessario ricreare la regola del prezzo di catalogo.

Di seguito è riportata una descrizione dettagliata dei passaggi richiesti:

1. [Applicare la patch](#patch).
1. In Commerce Admin, elimina la regola del prezzo di catalogo relativa al problema (dove è stata aggiornata l’ora di inizio). A questo scopo, apri la pagina della regola in **Marketing** > **Promozioni** > **Regola prezzo catalogo** e fai clic su **Elimina regola**.
1. Se si accede al database, eliminare manualmente il record correlato dalla tabella `catalogrule`.
1. Correggere i collegamenti non validi nel database. Per ulteriori dettagli, vedere il [paragrafo correlato](#fix_links).
1. Nell&#39;amministratore di Commerce in **Marketing**, vai a **Promozioni** > **Regola prezzo catalogo** e crea la nuova regola con la configurazione richiesta.
1. Cancella la cache del browser in **Sistema** > **Gestione cache**.
1. Assicurati che i processi cron siano configurati correttamente e che possano essere eseguiti correttamente.

## Patch {#patch}

La patch è allegata a questo articolo. Per scaricarlo, scorri verso il basso fino alla fine dell’articolo e fai clic sul nome del file, oppure fai clic sul seguente collegamento:

[Scarica MDVA-7392\_EE\_2.2.1\_COMPOSER\_v2.patch](assets/MDVA-7392_EE_2.2.1_COMPOSER_v2.patch.zip)

## Versioni compatibili di Adobe Commerce:

La patch è stata creata per:

* Adobe Commerce 2.2.1

La patch è compatibile (ma potrebbe non risolvere il problema) anche con le seguenti versioni ed edizioni di Adobe Commerce:

* Adobe Commerce sull’infrastruttura cloud 2.2.0 - 2.2.4
* Adobe Commerce on-premise 2.2.0 e 2.2.2 - 2.2.4

## Come applicare il cerotto

Per istruzioni, vedere [Come applicare una patch del compositore fornita dall&#39;Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) nella Knowledge Base di supporto.

## Correzione dei collegamenti non validi alla gestione temporanea nel database {#fix_links}

>[!WARNING]
>
>Si consiglia vivamente di creare un backup del database prima di qualsiasi manipolazione del database. Consigliamo inoltre di testare prima le query nell’ambiente di sviluppo.

Eseguire la procedura seguente per correggere le righe con collegamenti non validi alla tabella `staging_update`.

1. Verificare se nella tabella `flag` sono presenti collegamenti non validi alla tabella `staging_update`. Si tratta di record in cui `flag_code=staging`.
1. Identificare la versione non valida dalla tabella `flag` utilizzando la query seguente:

   ```sql
   SELECT flag_data FROM flag WHERE flag_code = 'staging';
   ```

1. Dalla tabella `staging_update`, selezionare la versione esistente che è minore della versione corrente (non valida) e recuperare il valore della versione che è due numeri. È possibile utilizzare questa versione, non quella precedente, per evitare che la versione precedente sia la versione massima della tabella `staging_update` che può essere applicata e che sia necessario riapplicarla.

   ```sql
   SELECT id FROM staging_update WHERE id < %current_id% ORDER BY id DESC LIMIT 1, 1
   ```

   La versione ricevuta in risposta è la versione valida `id`.

1. Per le righe con collegamenti non validi nella tabella `flag`, impostare i valori `flag_data` su dati che conterranno un ID versione valido. Questo consente di risparmiare le prestazioni nella fase di reindicizzazione e di evitare la reindicizzazione di tutte le entità.

   ```sql
   UPDATE flag SET flag_data=REPLACE(flag_data, '%invalid_id%', '%new_valid_id%') WHERE flag_code='staging';
   ```

<u>Esempio:</u>

```sql
SELECT flag_data FROM flag WHERE flag_code = 'staging'; <code class="language-bash">Response < 2.2 version</code>
```

```bash
+-------------------------------------------------+
```

```bash
| flag_data                                       |
```

```bash
+-------------------------------------------------+
```

```bash
| a:1:{s:15:"current_version";s:10:"1490005140";} |
```

```bash
+-------------------------------------------------+
```

```bash
Response from 2.2 version
```

```bash
+-------------------------------------------------+
```

```bash
| flag_data                                       |
```

```bash
+-------------------------------------------------+
```

```bash
| {"current_version":"1490005140"} |
```

```bash
+-------------------------------------------------+
```

```sql
SELECT id FROM staging_update WHERE id < 1490005140 <code class="language-sql">ORDER BY id DESC LIMIT 1, 1</code>;
```

```bash
Response:
```

```bash
1490005138
```

```sql
UPDATE flag SET flag_data=REPLACE(flag_data, '1490005140', '1490005138') WHERE flag_code='staging';
```

## File allegati
