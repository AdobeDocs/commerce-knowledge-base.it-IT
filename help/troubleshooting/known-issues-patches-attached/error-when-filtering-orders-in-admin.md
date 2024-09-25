---
title: Errore durante il filtraggio degli ordini nell’amministratore
description: Questo articolo fornisce una patch per il problema di Adobe Commerce, in cui si verifica un errore quando si tenta di filtrare gli ordini in Admin by date, visualizzando il messaggio "Violazione del vincolo di integrità 1052 Colonna 'created_at' dove la clausola è ambigua".
feature: Orders
role: Developer
source-git-commit: e5eb65b23afaed4658f8576c747f11a31a8ec1aa
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# Errore durante il filtraggio degli ordini nell’amministratore

Questo articolo fornisce una patch per il problema di Adobe Commerce in cui si verifica un errore durante il tentativo di filtrare gli ordini in Admin by date, visualizzando il messaggio: *Violazione del vincolo di integrità: 1052 Colonna &#39;created_at&#39; dove la clausola è ambigua*.

## Versioni interessate

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7

## Problema

Il filtro degli ordini nella data Admin by restituisce un errore.

Il file exception.log mostra quanto segue:

```SQL
report.CRITICAL: PDOException: SQLSTATE[23000]: Integrity constraint violation: 1052 Column 'created_at' in where clause is ambiguous in /path/to/magento/vendor/magento/framework/DB/Statement/Pdo/Mysql.php:90
```

<u>Passaggi da riprodurre:</u>

1. Vai a **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
   * Imposta l&#39;ordine **[!UICONTROL Purchase Date Ascending]** nella griglia, OPPURE
   * Imposta **[!UICONTROL Purchase Date Filter]** nei filtri.

1. Si è verificato un errore: *Si è verificato un errore durante l&#39;elaborazione della visualizzazione predefinita ed è stato ripristinato lo stato originale del filtro.*

## Causa

Problema con i moduli [!DNL PayPal Braintree].

## Soluzione

Per risolvere il problema, applica la patch allegata a questo articolo. Per scaricarlo, scorri verso il basso fino alla fine dell’articolo e fai clic sul nome del file, oppure fai clic sul seguente collegamento:

[bundle_3357_filter_order_in_admin_by_date_patch.zip](assets/bundle-3357-unable-to-filter-order-in-admin-by-date.zip)

La patch è compatibile con tutte le versioni e le edizioni interessate.

## Come applicare il cerotto

Per istruzioni, vedere [Come applicare una patch del compositore fornita dall&#39;Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) nella Knowledge Base di supporto.
