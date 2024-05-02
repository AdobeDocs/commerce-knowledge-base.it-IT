---
title: "Patch MDVA-28409: arresto anomalo del server web Adobe Commerce - Memoria insufficiente"
description: La patch MDVA-28409 risolve il problema relativo all'interruzione del processo cron per la rimozione delle virgolette a causa della necessità di elaborare un numero elevato di elementi. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.5.
exl-id: 175e5f2f-2f76-42ee-83e9-c1b23ff81e96
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# Patch MDVA-28409: arresto anomalo del server web Adobe Commerce - Memoria insufficiente

La patch MDVA-28409 risolve il problema relativo all&#39;interruzione del processo cron per la rimozione delle virgolette a causa della necessità di elaborare un numero elevato di elementi. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.5.

## Prodotti e versioni interessati

Adobe Commerce on-premise e Adobe Commerce sull’infrastruttura cloud 2.3.4 - 2.3.5, 2.4.0

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il problema è che la memoria del processo cron è esaurita a causa della quantità di dati che il processo sta tentando di elaborare. I sintomi di questo problema includono prestazioni lente a causa dell&#39;elevato utilizzo del disco da parte di MySQL e della memoria insufficiente del server web.

<u>Passaggi da riprodurre:</u>

Per verificare se è presente un processo cron che non è in grado di rimuovere le virgolette obsolete, eseguire la query seguente:

```
select * from cron_schedule where job_code like '%sales_clean_quotes%'
```

<u>Risultato previsto:</u>

Lo stato di `sales_clean_quotes` il processo cron deve essere `success`.

<u>Risultato effettivo:</u>

Lo stato di `sales_clean_quotes` processo cron è `running` o `error`.

Un altro modo per confermare che esiste un processo cron che non è in grado di rimuovere le virgolette obsolete consiste nel mappare l’output della query da **Passaggio 1** (`executed_at`) rispetto alle marche temporali di eventuali errori di memoria in `/var/log/cron.log`. Se un processo cron non è in grado di elaborare la quantità di dati, è possibile che venga visualizzato un messaggio simile al seguente:

```
PHP Fatal error:  Allowed memory size of 1073741824 bytes exhausted (tried to allocate 4096 bytes) in /app/vendor/magento/framework/DB/Statement/Pdo/Mysql.php on line 91

Fatal error: Allowed memory size of 1073741824 bytes exhausted (tried to allocate 4096 bytes) in /app/vendor/magento/framework/DB/Statement/Pdo/Mysql.php on line 91
--
[2020-05-30 05:00:27.224718] Launching command 'php bin/magento cron:run'.
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sezione.
