---
title: "Problema noto di Adobe Commerce 2.4.0: test di integrazione non riusciti"
description: Questo articolo fornisce una patch per il problema di Adobe Commerce 2.4.0 in cui i test di integrazione non riescono perché la dichiarazione di "Dotdigitalgroup\Email\Test\Integration\Model\Sync\Importer\ImporterFailedTest::setUp()" non è compatibile con PHPUnit 9, utilizzato per la versione 2.4.0.
exl-id: 8e0ca2da-81d9-4561-a009-593240f46e41
feature: Integration
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Problema noto di Adobe Commerce 2.4.0: test di integrazione non riusciti

Questo articolo fornisce una patch per il problema di Adobe Commerce 2.4.0 in cui i test di integrazione non riescono a causa della dichiarazione di `Dotdigitalgroup\Email\Test\Integration\Model\Sync\Importer\ImporterFailedTest::setUp()` non è compatibile con PHPUnit 9, utilizzato per la versione 2.4.0.

## Prodotti e versioni interessati

* Adobe Commerce sull’infrastruttura cloud 2.4.0
* Adobe Commerce on-premise 2.4.0

## Problema

<u>Passaggi da riprodurre</u>

Eseguire gli integration test 2.4.0.

<u>Risultato previsto</u>

Test superati.

<u>Risultato effettivo</u>

*Errore irreversibile PHP: la dichiarazione di Dotdigitalgroup\\Email\\Test\\Integration\\Model\\Sync\\Importer\\ImporterFailedTest::setUp() deve essere compatibile con PHPUnit\\Framework\\TestCase::setUp(): void in /var/www/vendor/dotmailer/dotmailer-magento2-extension/Test/Integration/Model/Sync/Importer/ImporterFailedTest.php alla riga 36*

## Soluzione

Applichi la patch fornita in questo articolo.

## Patch

La patch è allegata a questo articolo. Per scaricarlo, scorri verso il basso fino alla fine dell’articolo e fai clic sul nome del file, oppure fai clic sul seguente collegamento:

[BUNDLE-2684-composer.patch](assets/BUNDLE-2684-composer.patch.zip)

### Versioni compatibili di Adobe Commerce:

La patch è stata creata per:

* Adobe Commerce sull’infrastruttura cloud 2.4.0
* Adobe Commerce on-premise 2.4.0

## Come applicare il cerotto

Consulta [Come applicare una patch del compositore fornita dall&#39;Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) nella knowledge base di supporto per le istruzioni.

## File allegati
