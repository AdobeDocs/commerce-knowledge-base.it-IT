---
title: Adobe Commerce per errori di processi cron di Reporting avanzato
description: Questo articolo fornisce patch per i problemi dei processi cron di Advanced Reporting in Adobe Commerce, che possono causare un errore 404 per i clienti che tentano di accedere a Advanced Reporting.
exl-id: c11a5faf-a243-411a-af0f-585a401e6e39
feature: Cache
role: Developer
source-git-commit: 6287e708c830680e04dd068b64cf63ca13ecdedb
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Adobe Commerce per errori di processi cron di Reporting avanzato

Questo articolo fornisce patch per i problemi dei processi cron di Advanced Reporting in Adobe Commerce, che possono causare un errore 404 per i clienti che tentano di accedere a Advanced Reporting.

## Prodotti e versioni interessati

Adobe Commerce (tutte le opzioni di implementazione) 2.3.x

## Problema

Un cliente riceve un errore 404 quando tenta di accedere al Reporting avanzato e sono presenti errori nei registri associati a `analytics_collect_data job`.

## Versioni compatibili del Magento:

Le patch sono compatibili (ma potrebbero non risolvere il problema) con le seguenti versioni di Adobe Commerce:

* [MDVA-19391\_EE\_2.3.1\_COMPOSER\_v1.patch](assets/MDVA-19391_EE_2.3.1_COMPOSER_v1.patch.zip): Adobe Commerce (tutte le opzioni di distribuzione) 2.3.1-2.3.4-p2
* [MDVA-18980\_EE\_2.2.6\_COMPOSER\_v1.patch](assets/MDVA-18980_EE_2.2.6_COMPOSER_v1.patch.zip): Adobe Commerce (tutte le opzioni di distribuzione) 2.3.0
* [MDVA-15136\_EE\_2.2.6\_COMPOSER\_v1.patch](assets/MDVA-15136_EE_2.2.6_COMPOSER_v1.patch.zip): Adobe Commerce (tutte le opzioni di distribuzione) 2.3.0

## **Soluzione**

Per risolvere il problema, applicare la patch pertinente allegata a questo articolo. Per scaricarlo, fai clic sui seguenti collegamenti:

* Scarica [MDVA-19391\_EE\_2.3.1\_COMPOSER\_v1.patch](assets/MDVA-19391_EE_2.3.1_COMPOSER_v1.patch.zip)
* Scarica [MDVA-15136\_EE\_2.2.6\_COMPOSER\_v1.patch](assets/MDVA-15136_EE_2.2.6_COMPOSER_v1.patch.zip)
* Scarica [MDVA-18980\_EE\_2.3.1\_COMPOSER\_v1.patch](assets/MDVA-18980_EE_2.2.6_COMPOSER_v1.patch.zip)

Per verificare quale cerotto usare:

<ol><li>Esaminare i registri utilizzando il comando seguente:<code>grep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz</code>
</li><li>A seconda dell’errore visualizzato, seleziona una patch utilizzando le informazioni riportate nella tabella seguente.<table style="width: 826px;">
<tbody>
<tr>
<td class="wysiwyg-text-align-center">
<p>Errore</p>
</td>
<td class="wysiwyg-text-align-center">Patch</td>
</tr>
<tr>
<td>
<pre>report.CRITICAL: Errore durante l'esecuzione di un processo cron {"exception":"[object] (RuntimeException(code:
  0): errore durante l’esecuzione di un processo cron in /srv/public_html/vendor/magento/module-cron/Observer/ProcessCronQueueObserver.php:327,
  TypeError(code: 0): substr_count() prevede che il parametro 1 sia una stringa, dato null
  in /srv/public_html/vendor/magento/module-page-builder-analytics/Model/ContentTypeUsageReportProvider.php:106)"}
  []</pre>OPPURE<pre>report.ERROR: Errore di analytics_collect_data del processo del connettore: substr_count() Expects
  il parametro 1 deve essere una stringa, è stato fornito un valore null. Statistiche: {"sum":0,"count":1,"realmem":0,"emalloc":0,"realmem_start":224919552,"emalloc_start":216398384}
  [] []</pre>
<p> </p>
</td>
<td>Applica<a href="assets/MDVA-19391_EE_2.3.1_COMPOSER_v1.patch">MDVA-19391_EE_2.3.1_COMPOSER_v1.patch.zip</a>, cancella la cache e attendi 24 ore prima che il processo venga eseguito di nuovo e riprova.</td>
</tr>
<tr>
<td>
<p><em>Impossibile aprire il file /tmp/analytics/tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../</em></p>
</td>
<td>Applica<a href="assets/MDVA-15136_EE_2.2.6_COMPOSER_v1.patch">MDVA-15136_EE_2.2.6_COMPOSER_v1.patch.zip</a>, cancella la cache e attendi 24 ore prima che il processo venga eseguito di nuovo e riprova.</td>
</tr>
<tr>
<td><em>Crittografia non valida</em></td>
<td>Applica<a href="assets/MDVA-18980_EE_2.2.6_COMPOSER_v1.patch">MDVA-18980_EE_2.2.6_COMPOSER_v1.patch.zip</a>, cancella la cache e attendi 24 ore prima che il processo venga eseguito di nuovo e riprova.</td>
</tr>
</tbody>
</table>
</li></ol>

## Come applicare il cerotto

Decomprimere il file e seguire le istruzioni in [Come applicare una patch del compositore fornita dall&#39;Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).

## Lettura correlata

[Impossibile eliminare il file. Attenzione!unlink: errore di file o directory non presente dall&#39;amministratore](/help/troubleshooting/miscellaneous/file-cannot-be-deleated-no-file-or-directory.md)
