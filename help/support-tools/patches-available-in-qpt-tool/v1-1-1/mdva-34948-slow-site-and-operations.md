---
title: "MDVA-34948: rallentamento del sito web"
description: La patch di MDVA-34948 Adobe Commerce risolve il problema del rallentamento del sito Web. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1. L'ID della patch è MDVA-34948. Il problema è stato risolto nella versione 2.4.1 di Adobe Commerce.
exl-id: ba5417b3-a71c-4f1b-877b-4e7206f86660
feature: Observability, Configuration
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# MDVA-34948: rallentamento del sito web


## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce sulla nostra infrastruttura cloud 2.4.0-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce on-premise e Adobe Commerce sulla nostra infrastruttura cloud 2.3.6-2.3.6-p1, 2.4.0-2.4.0-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il sito web è lento, il che ostacola le operazioni.

<u>Passaggi da riprodurre</u>:

1. Esegui `show processlist` in MySQL.
1. Verifica se sono presenti più query come:

```sql
   SELECT GET_LOCK(SYSTEM_CONFIG', '10');
```

<u>Risultati previsti</u>:

`GET_LOCK` deve essere eseguito immediatamente.

<u>Risultati effettivi</u>:

Più `GET_LOCK` le query si bloccano per un massimo di 10 secondi ciascuna.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sezione.
