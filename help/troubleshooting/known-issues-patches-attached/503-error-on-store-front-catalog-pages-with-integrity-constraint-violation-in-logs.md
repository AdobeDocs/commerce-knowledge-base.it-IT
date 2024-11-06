---
title: Errore 503 nelle pagine del catalogo principale dell’archivio con "Violazione del vincolo di integrità" nei registri
description: Questo articolo fornisce una patch per il problema noto di Adobe Commerce on cloud infrastructure 2.2.0 relativo all’inaccessibilità delle pagine del catalogo principale dei negozi.
exl-id: ad363744-756a-48b9-ae11-58642e0ca6a4
feature: Catalog Management, Logs
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# Errore 503 nelle pagine del catalogo principale dell’archivio con &quot;Violazione del vincolo di integrità&quot; nei registri

>[!NOTE]
>
>Questo articolo fornisce una patch come soluzione alternativa, ma il problema è stato risolto definitivamente in Adobe Commerce on cloud infrastructure v2.3.3 ed è consigliabile effettuare l’aggiornamento alla versione v2.3.3. Segui i passaggi descritti in [Aggiornare Adobe Commerce versione](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) nella documentazione per gli sviluppatori.

Questo articolo fornisce una patch per il problema noto di Adobe Commerce on cloud infrastructure 2.2.0 relativo all&#39;archiviazione delle pagine del catalogo principale che non è accessibile. Il messaggio di errore nel registro è simile al seguente: *Violazione del vincolo di integrità: 1062 Voce duplicata &#39;%entry%&#39; per la chiave &#39;PRIMARY&#39;. Query: INSERT INTO \`search\_tmp\_%number%*.

## Problema

Le pagine del catalogo principale del negozio diventano inaccessibili in modo imprevisto. Il log degli errori presenta una descrizione simile alla seguente: *Violazione del vincolo di integrità: 1062 Voce duplicata &#39;%entry%&#39; per la chiave &#39;PRIMARY&#39;, query: INSERT INTO \`search\_tmp\_%number%*.

Il problema è correlato alla ricerca e causato dall’esistenza dell’indice obsoleto insieme a quello nuovo dopo la reindicizzazione.

## Soluzione

Per risolvere il problema, è necessario rimuovere gli indici obsoleti da Elasticsearch e applicare la patch per evitare che vengano visualizzati.

Per elencare tutti gli indici, utilizzare il comando seguente:

<pre>curl -X GET %elasticsearch_domain%:%elasticsearch_port%/_cat/indices</pre>

Per rimuovere gli indici obsoleti, individuarli nel database e quindi utilizzare il comando seguente:

```bash
curl -X DELETE %elasticsearch_domain%:%elasticsearch_port%/%product_id%_v%outdated_version%
```

Esempio:

```bash
curl -X DELETE 127.0.0.1:9200/magento2_product_8_v332
```

## Patch

Le patch sono allegate a questo articolo. Per scaricare una patch, scorri verso il basso fino alla fine dell’articolo e fai clic sul nome del file richiesto, oppure fai clic su uno dei seguenti collegamenti:

[Scarica MDVA-9590\_EE\_2.2.0\_COMPOSER\_v2.patch](assets/MDVA-9590_EE_2.2.0_COMPOSER_v2.patch.zip)

[Scarica MDVA-13203\_EE\_2.2.4\_V1\_COMPOSER.patch](assets/MDVA-13203_EE_2.2.4_V1_COMPOSER.patch.zip)

## Versioni compatibili di Adobe Commerce

Le patch sono state create per le edizioni e le versioni seguenti:

* Adobe Commerce sull&#39;infrastruttura cloud 2.2.0 (`MDVA-9590_EE_2.2.0_COMPOSER_v2.patch`)
* Adobe Commerce sull&#39;infrastruttura cloud 2.2.4 (`MDVA-13203_EE_2.2.4_V1_COMPOSER.patch`)

La patch `MDVA-9590_EE_2.2.0_COMPOSER_v2` è compatibile (ma potrebbe non risolvere il problema) anche con le seguenti versioni ed edizioni di Adobe Commerce:

* Adobe Commerce su infrastruttura cloud 2.0.X, 2.1.X, 2.2.X e 2.3.0 - 2.3.3
* Adobe Commerce on-premise 2.0.X, 2.1.X, 2.2.X e 2.3.0 - 2.3.3

La patch `MDVA-13203_EE_2.2.4_V1_COMPOSER` è compatibile (ma potrebbe non risolvere il problema) anche con le seguenti versioni ed edizioni di Adobe Commerce:

* Adobe Commerce su infrastruttura cloud 2.0.X, 2.1.X, 2.2.X e 2.3.0 - 2.3.3
* Adobe Commerce on-premise 2.0.X, 2.1.X, 2.2.X e 2.3.0 - 2.3.3

## Come applicare il cerotto

Per istruzioni, vedere [Come applicare una patch del compositore fornita da Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) nella Knowledge Base di supporto.

## Collegamenti utili

* [Percorso dei file di registro per Adobe Commerce sull&#39;infrastruttura cloud Architettura del piano iniziale](/help/how-to/general/log-locations-directories-for-starter-plan.md) nella knowledge base di supporto.
* [Percorso dei file di registro per Adobe Commerce sull&#39;infrastruttura cloud Architettura del piano Pro](/help/how-to/general/log-locations-directories-for-pro-plan-integration-staging-production.md) nella knowledge base di supporto.
* [Percorso dei file di registro per Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations) nella documentazione per gli sviluppatori.

## File allegati
