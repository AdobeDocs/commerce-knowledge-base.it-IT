---
title: "MDVA-30102: cache Redis piena"
description: La patch MDVA-30102 risolve il problema della cache Redis, che diventa piena e genera errori, causando problemi con le pagine di elenco dei prodotti (PLP) e le pagine di dettagli del prodotto (PDP), come i prodotti mancanti. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.6.
exl-id: 34772296-8c93-471c-b5ad-6815adb78ca6
feature: Cache, Categories, Services
role: Admin
source-git-commit: 324cce66df1e4ab7ec4ef8fb6512c3acbabdf3ab
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 0%

---

# MDVA-30102: cache Redis piena

La patch MDVA-30102 risolve il problema della cache Redis, che diventa piena e genera errori, causando problemi con le pagine di elenco dei prodotti (PLP) e le pagine di dettagli del prodotto (PDP), come i prodotti mancanti. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce sull’infrastruttura cloud 2.3.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.2 - 2.4.1-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La cache Redis si sta esaurendo e l&#39;allocazione di `maxmemory` sembra insufficiente. La cache di layout non aveva TTL e non è stata eliminata, causando la crescita della cache e l’eliminazione di altre chiavi in Redis. Di conseguenza, tutta la memoria Redis è stata allocata per la cache di layout.

<u>Prerequisiti</u>:

* L’utente deve utilizzare Adobe Commerce 2.4 e disporre di 100.000 prodotti semplici (il tipo di prodotto non conta) e 50 categorie.
* La cache Redis deve essere configurata in base ai passaggi forniti in [Guida alla configurazione di Adobe Commerce > Usa Redis per la pagina Adobe Commerce e cache predefinita](https://devdocs.magento.com/guides/v2.4/config-guide/redis/redis-pg-cache.html#example-command) nella documentazione per gli sviluppatori.

<u>Passaggi da riprodurre</u>:

1. Sfoglia tutti i PDP e i PLP. È possibile utilizzare [OWASP ZAP](https://www.zaproxy.org/) per eseguire la ricerca per indicizzazione del sito.
1. Osservare l&#39;utilizzo della memoria Redis.
1. Controllare inoltre la configurazione corrente e la memoria utilizzata. Eseguire il comando seguente in CLI. Verifica la memoria utilizzata, la memoria massima, le chiavi eliminate e il tempo di attività Redis in giorni:

```
redis-cli -p REDIS_PORT -h REDIS_HOST info | egrep --color "(role|used_memory_peak|maxmemory|evicted_keys|uptime_in_days)"
```

<u>Risultati previsti</u>:

La cache Redis non dovrebbe crescere rapidamente.

<u>Risultati effettivi</u>:

La cache Redis cresce fino a circa 5 GB. Esiste un limite massimo di 8 GB di memoria Redis, quindi se si dispone di prodotti da 1 milione di unità, la memoria si esaurisce molto rapidamente.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
