---
title: Aggiornamento Adobe Commerce 2.4.3, 2.3.7-p1 PHP Errore irreversibile Hotfix
description: "Questo articolo corregge il seguente errore che si verifica quando gli esercenti tentano di eseguire l’aggiornamento ad Adobe Commerce (tutti i metodi di distribuzione) o al Magento Open Source 2.4.3 o 2.3.7-p1:"
exl-id: 1c472214-8387-403e-b2d2-d3f3c9e1da6a
feature: Install, Upgrade
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# Aggiornamento Adobe Commerce 2.4.3, 2.3.7-p1 PHP Errore irreversibile Hotfix

Questo articolo corregge il seguente errore: quando gli esercenti tentano di eseguire l’aggiornamento ad Adobe Commerce (tutti i metodi di distribuzione) o al Magento Open Source 2.4.3 o 2.3.7-p1:

*Errore irreversibile PHP: errore non rilevato: chiamata a funzione non definita Magento\Framework\Filesystem\Directory\str_contains() in &lt;...>/magento/vendor/magento/framework/Filesystem/Directory/DenyListPathValidator.php:74*

Il problema verrà risolto nell’ambito delle versioni 2.4.4, 2.4.3-p1 e 2.3.7-p2.

## Versioni e prodotti interessati

* Adobe Commerce (tutti i metodi di distribuzione) durante l’aggiornamento a 2.3.7-p1 o 2.4.3.
* Magento Open Source durante l’aggiornamento a 2.3.7-p1 o 2.4.3.

## Problema

Il problema è causato dalle nuove versioni di Adobe Commerce 2.4.3 e 2.3.7-p1 che utilizzano solo la funzione PHP 8 `str_contains`. Adobe Commerce 2.4.3 e 2.3.7-p1 sono compatibili solo con PHP 7.4, pertanto questa funzione non può essere utilizzata.

<u>Passaggi da riprodurre</u> :

Tentativo di aggiornamento ad Adobe Commerce 2.4.3 o 2.3.7-p1.

<u>Risultato previsto:</u>

Aggiornamento riuscito.

<u>Risultato effettivo:</u>

Errore irreversibile PHP.

## Soluzione

Come soluzione alternativa è possibile eseguire il comando seguente in CLI/Terminal: `composer require symfony/polyfill-php80` dalla cartella principale del Magento o installare una patch del compositore.

Per risolvere il problema della versione 2.4.3, Adobe Commerce (tutti i metodi di distribuzione) e gli esercenti di Magento Open Source devono applicare la patch:

[AC-384_Fix_Incompatible_PHP_Method__2.4.3_ce.patch](assets/AC-384__Fix_Incompatible_PHP_Method__2.4.3_ce.patch.zip)

Per risolvere il problema della versione 2.3.7-p1, Adobe Commerce (tutti i metodi di distribuzione) e gli esercenti di Magento Open Source devono applicare la patch:

[AC-384__Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch](assets/AC-384__Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch.zip)

## Come applicare il cerotto

Consulta [Come applicare una patch del compositore fornita dal Magento](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) per istruzioni.

## Lettura correlata

GitHub [Comando PHP 8 non supportato nel Magento 2.4.3 EE #33680](https://github.com/magento/magento2/issues/33680)
