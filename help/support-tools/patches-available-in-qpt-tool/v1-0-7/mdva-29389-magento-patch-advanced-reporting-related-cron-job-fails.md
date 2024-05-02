---
title: "MDVA-29389: errore del processo cron correlato a Reporting avanzato"
description: '"La patch MDVA-29389 risolve il problema in cui con Advanced Reporting, dove il cronjob "analytics_collect_data" afferma: "*La porta deve essere configurata all’interno del parametro host (come localhost:3306)*". Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7. L''ID della patch è MDVA-29389. Il problema è stato risolto in Adobe Commerce 2.4.2."'
exl-id: eee909d5-9d0d-46b6-846a-665f89db0eee
feature: Cache
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# MDVA-29389: errore del processo cron correlato a Reporting avanzato

La patch di MDVA-29389 risolve il problema in cui con la funzionalità di Advanced Reporting, `analytics_collect_data` cronjob scrive: &quot;*La porta deve essere configurata all&#39;interno del parametro host (come localhost:3306)*&quot;. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7. L&#39;ID della patch è MDVA-29389. Il problema è stato risolto in Adobe Commerce 2.4.2.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.4.

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.1.

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Passaggi da riprodurre</u>:

1. Nell’istanza di Adobe Commerce, abilita Reporting avanzato.
1. Esegui la query seguente per inserire il valore analytics/general/token nel database:

   ```sql
   INSERT INTO core_config_data VALUES(NULL,'default',0,'analytics/general/token','ABCDE',now());
   ```

1. Apri il file env.php e aggiungi una porta al parametro host nella configurazione DB nel formato seguente: `'host' => 'hostname:port',`
1. Cancella cache.
1. Esegui il `analytics_collect_data` lavoro cron.

<u>Risultati previsti</u>:

Il `analytics_collect_data` Il processo viene eseguito correttamente quando si utilizza una porta predefinita o non predefinita per la connessione a MySQL in env.php.

<u>Risultati effettivi</u>:

Il `analytics_collect_data` il processo genera un errore&quot;*La porta deve essere configurata all&#39;interno del parametro host (come localhost:3306)*&quot; quando si utilizza una porta non predefinita per la connessione a MySQL in env.php.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
