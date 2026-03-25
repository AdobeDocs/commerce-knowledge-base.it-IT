---
title: Aggiornamento Adobe Commerce 2.4.3, 2.3.7-p1 PHP Errore irreversibile Hotfix
description: 'Questo articolo fornisce una correzione per consentire agli esercenti che tentano di eseguire l’aggiornamento ad Adobe Commerce (tutti i metodi di distribuzione) o a Magento Open Source 2.4.3 o 2.3.7-p1 di visualizzare il seguente errore:'
exl-id: 1c472214-8387-403e-b2d2-d3f3c9e1da6a
feature: Install, Upgrade
role: Developer
source-git-commit: 1dcd003bd9b08741c0fba464f5520797cfaeccbb
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# Aggiornamento Adobe Commerce 2.4.3, 2.3.7-p1 PHP Errore irreversibile Hotfix

Questo articolo fornisce una correzione per consentire agli esercenti che tentano di eseguire l’aggiornamento ad Adobe Commerce (tutti i metodi di distribuzione) o a Magento Open Source 2.4.3 o 2.3.7-p1 di visualizzare il seguente errore:

*Errore irreversibile PHP: errore non rilevato: chiamata a una funzione non definita Magento\Framework\Filesystem\Directory\str_contains() in &lt;...>/magento/vendor/magento/framework/Filesystem/Directory/DenyListPathValidator.php:74*

Il problema verrà risolto nell’ambito delle versioni 2.4.4, 2.4.3-p1 e 2.3.7-p2.

## Versioni e prodotti interessati

* Adobe Commerce (tutti i metodi di distribuzione) durante l’aggiornamento a 2.3.7-p1 o 2.4.3.
* Magento Open Source durante l’aggiornamento a 2.3.7-p1 o 2.4.3.

## Problema

Il problema è causato dalle nuove versioni di Adobe Commerce 2.4.3 e 2.3.7-p1 che utilizzano solo la funzione PHP 8 `str_contains`. Adobe Commerce 2.4.3 e 2.3.7-p1 sono compatibili solo con PHP 7.4, pertanto questa funzione non può essere utilizzata.

<u>Passaggi da riprodurre</u>:

Tentativo di aggiornamento ad Adobe Commerce 2.4.3 o 2.3.7-p1.

<u>Risultato previsto:</u>

Aggiornamento riuscito.

<u>Risultato effettivo:</u>

Errore irreversibile PHP.

## Soluzione

Come soluzione alternativa è possibile eseguire il comando seguente in CLI/Terminal: `composer require symfony/polyfill-php80` dalla cartella principale di Magento oppure installare una patch del compositore.

Per risolvere il problema della versione 2.4.3, Adobe Commerce (tutti i metodi di distribuzione) e i rivenditori Magento Open Source devono applicare la patch:

[AC-384_Fix_Incompatible_PHP_Method__2.4.3_ce.patch](assets/AC-384__Fix_Incompatible_PHP_Method__2.4.3_ce.patch.zip)

Per risolvere il problema della versione 2.3.7-p1, Adobe Commerce (tutti i metodi di distribuzione) e i rivenditori Magento Open Source devono applicare la patch:

[AC-384__Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch](assets/AC-384__Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch.zip)

## Come applicare il cerotto

Per istruzioni, vedere [Come applicare una patch del compositore fornita da Magento](https://experienceleague.adobe.com/it/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/how-to-apply-a-composer-patch-provided-by-magento).

## Lettura correlata

Comando GitHub [PHP 8 non supportato in Magento 2.4.3 EE #33680](https://github.com/magento/magento2/issues/33680)
