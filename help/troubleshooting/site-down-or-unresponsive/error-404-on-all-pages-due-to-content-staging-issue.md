---
title: Errore 404 su tutte le pagine a causa di un problema di gestione temporanea del contenuto
description: Questo articolo fornisce una correzione per il problema di infrastruttura cloud di Adobe Commerce on-premise e Adobe Commerce, in cui viene visualizzato un errore 404 durante l’accesso a qualsiasi pagina storefront o all’amministratore Commerce.
exl-id: 62d8ba6e-8550-4e1e-8e8d-8f319c92778a
feature: CMS, Catalog Management, Categories, Page Content, Staging
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 0%

---

# Errore 404 su tutte le pagine a causa di un problema di gestione temporanea del contenuto

Questo articolo fornisce una correzione per il problema di infrastruttura cloud di Adobe Commerce on-premise e Adobe Commerce, in cui viene visualizzato un errore 404 durante l’accesso a qualsiasi pagina storefront o all’amministratore Commerce.

## Prodotti e versioni interessati

* Adobe Commerce on-premise 2.2.x, 2.3.x
* Adobe Commerce sull’infrastruttura cloud 2.2.x, 2.3.x

## Problema

>[!NOTE]
>
>Questo articolo non si applica alla situazione in cui si verifica un errore 404 quando si tenta di [anteprima dell’aggiornamento della gestione temporanea](https://docs.magento.com/user-guide/cms/content-staging-scheduled-update.html#preview-the-scheduled-change). Se riscontri questo problema, apri una [ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

L’accesso a qualsiasi pagina della vetrina o all’amministratore genera l’errore 404 (pagina &quot;Ops, le nostre cattive...&quot;) dopo aver eseguito operazioni con aggiornamenti pianificati per archiviare le risorse di contenuto utilizzando [Staging dei contenuti](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html) (aggiornamenti per le risorse di contenuto del negozio pianificate utilizzando [Magento\_Modulo gestione temporanea](https://developer.adobe.com/commerce/php/module-reference/)). Ad esempio, potresti aver eliminato un prodotto con un aggiornamento pianificato o rimosso la data di fine per l’aggiornamento pianificato.

Una risorsa di contenuto store include:

* Prodotto
* Categoria
* Regola prezzo catalogo
* Regola prezzo carrello
* Pagina CMS
* Blocco CMS
* Widget

Alcuni scenari sono descritti nella sezione Causa seguente.

## Causa

Il `flag` nel database (DB) contiene collegamenti non validi al database `staging_update` tabella.

Il problema è relativo alla gestione temporanea dei contenuti. Di seguito sono riportati due scenari specifici; tieni presente che potrebbero verificarsi più situazioni che attivano il problema.

**Scenario 1** Eliminazione di una risorsa di contenuto store che:

* ha un aggiornamento pianificato con Content Staging
* l’aggiornamento ha una data di fine (ossia la data di scadenza dopo la quale la risorsa aggiornata torna alla versione precedente)
* la data di fine dell’aggiornamento è nel passato

Allo stesso tempo, il problema potrebbe non verificarsi se una risorsa eliminata non ha una data di fine per l’aggiornamento pianificato.

**Scenario 2** Rimozione della data/ora di fine di un aggiornamento pianificato.

### Identifica se il problema è correlato

Per verificare se il problema riscontrato è quello descritto in questo articolo, esegui la seguente query DB:

```sql
   SELECT f.flag_data >'$.current_version' as flag_version, (su.id IS NOT NULL) as update_exists
   -> FROM flag f
   -> LEFT JOIN staging_update su
   -> ON su.id = f.flag_data >'$.current_version'
   -> WHERE flag_code = 'staging';
```

Se la query restituisce una tabella in cui `update_exists` valore è &quot;0&quot;, quindi un collegamento non valido al `staging_update` presente nel database e i passaggi descritti nella [Sezione Soluzione](#solution) aiuterà a risolvere il problema. Di seguito è riportato un esempio del risultato della query con `update_exists` valore uguale a &quot;0&quot;:

![update_exists_0.png](assets/update_exists_0.png)

Se la query restituisce una tabella in cui `update_exists` se il valore è &quot;1&quot; o vuoto, significa che il problema non è correlato agli aggiornamenti di staging. Di seguito è riportato un esempio del risultato della query con `update_exists` valore uguale a &quot;1&quot;:

![updates_exist_1.png](assets/updates_exist_1.png)

In questo caso, puoi fare riferimento a [Risoluzione dei problemi di inattività del sito](/help/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.md) per suggerimenti sulla risoluzione dei problemi.

## Soluzione

1. Esegui la query seguente per eliminare il collegamento non valido al `staging_update` tabella:

   ```sql
   DELETE FROM flag WHERE flag_code = 'staging';
   ```

1. Attendere l&#39;esecuzione del processo cron (se configurato correttamente, può durare fino a cinque minuti) oppure eseguirlo manualmente se non si dispone di cron.

Il problema deve essere risolto subito dopo aver risolto il collegamento non valido. Se il problema persiste, [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
