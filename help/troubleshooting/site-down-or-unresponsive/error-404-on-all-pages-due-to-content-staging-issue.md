---
title: Errore 404 su tutte le pagine a causa di un problema di gestione temporanea del contenuto
description: Questo articolo fornisce una correzione per il problema di infrastruttura cloud di Adobe Commerce on-premise e Adobe Commerce in cui viene visualizzato un errore 404 durante l'accesso a qualsiasi pagina storefront o a [!UICONTROL Commerce Admin].
exl-id: 62d8ba6e-8550-4e1e-8e8d-8f319c92778a
feature: CMS, Catalog Management, Categories, Page Content, Staging
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# Errore 404 su tutte le pagine a causa di un problema di gestione temporanea del contenuto

Questo articolo fornisce una correzione per il problema di infrastruttura cloud di Adobe Commerce on-premise e Adobe Commerce in cui viene visualizzato un errore 404 durante l&#39;accesso a qualsiasi pagina storefront o a [!UICONTROL Commerce Admin].

## Prodotti e versioni interessati

* Adobe Commerce on-premise 2.2.x, 2.3.x
* Adobe Commerce sull’infrastruttura cloud 2.2.x, 2.3.x

## Problema

>[!NOTE]
>
>Questo articolo non è applicabile alla situazione in cui si verifica un errore 404 quando si tenta di [visualizzare in anteprima l&#39;aggiornamento della gestione temporanea](https://experienceleague.adobe.com/it/docs/commerce-admin/content-design/guide-overview#preview-the-scheduled-change). Se riscontri questo problema, apri un [ticket di supporto](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case).

L&#39;accesso a qualsiasi pagina della vetrina o all&#39;amministratore genera l&#39;errore 404 (la pagina &quot;Ops, le nostre cattive...&quot;) dopo aver eseguito operazioni con aggiornamenti pianificati per le risorse di contenuto del negozio utilizzando [Staging contenuto](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html?lang=it) (aggiornamenti per le risorse di contenuto del negozio pianificate utilizzando il modulo [Magento\_Staging](https://developer.adobe.com/commerce/php/module-reference/)). Ad esempio, potresti aver eliminato un prodotto con un aggiornamento pianificato o rimosso la data di fine per l’aggiornamento pianificato.

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

La tabella `flag` nel database (DB) contiene collegamenti non validi alla tabella `staging_update`.

Il problema è relativo alla gestione temporanea dei contenuti. Di seguito sono riportati due scenari specifici; tieni presente che potrebbero verificarsi più situazioni che attivano il problema.

**Scenario 1:** eliminazione di una risorsa di contenuto dell&#39;archivio che:

* ha un aggiornamento pianificato con Content Staging
* l’aggiornamento ha una data di fine (ossia la data di scadenza dopo la quale la risorsa aggiornata torna alla versione precedente)
* la data di fine dell’aggiornamento è nel passato

Allo stesso tempo, il problema potrebbe non verificarsi se una risorsa eliminata non ha una data di fine per l’aggiornamento pianificato.

**Scenario 2:** Rimozione della data/ora di fine di un aggiornamento pianificato.

### Identifica se il problema è correlato

Per verificare se il problema riscontrato è quello descritto in questo articolo, esegui la seguente query DB:

```sql
   SELECT f.flag_data >'$.current_version' as flag_version, (su.id IS NOT NULL) as update_exists
   -> FROM flag f
   -> LEFT JOIN staging_update su
   -> ON su.id = f.flag_data >'$.current_version'
   -> WHERE flag_code = 'staging';
```

Se la query restituisce una tabella in cui il valore `update_exists` è &quot;0&quot;, nel database esiste un collegamento non valido alla tabella `staging_update` e i passaggi descritti nella [sezione Soluzione](#solution) aiuteranno a risolvere il problema. Di seguito è riportato un esempio del risultato della query con valore `update_exists` uguale a &quot;0&quot;:

![update_exists_0.png](assets/update_exists_0.png)

Se la query restituisce una tabella in cui il valore `update_exists` è &quot;1&quot; o un risultato vuoto, significa che il problema non è correlato agli aggiornamenti della gestione temporanea. Di seguito è riportato un esempio del risultato della query con valore `update_exists` uguale a &quot;1&quot;:

![aggiornamenti_exists_1.png](assets/updates_exist_1.png)

In questo caso, è possibile fare riferimento a [Risoluzione dei problemi di inattività del sito](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter) per informazioni sulla risoluzione dei problemi.

## Soluzione

1. Eseguire la query seguente per eliminare il collegamento non valido alla tabella `staging_update`:

   ```sql
   DELETE FROM flag WHERE flag_code = 'staging';
   ```

1. Attendere l&#39;esecuzione del processo [!DNL cron] (se configurato correttamente, può durare fino a cinque minuti) oppure eseguirlo manualmente se non è stato configurato [!DNL cron].

Il problema deve essere risolto subito dopo aver risolto il collegamento non valido. Se il problema persiste, [invia un ticket di supporto](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case).

## Lettura correlata

[Best practice per la modifica delle tabelle del database](https://experienceleague.adobe.com/it/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) nel playbook di implementazione di Commerce
