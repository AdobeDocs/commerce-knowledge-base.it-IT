---
title: "MDVA-31307: memoria insufficiente in alcune categorie"
description: La patch MDVA-31307 risolve il problema in cui "Magento\_Csp/Model/BlockCache" consuma molta memoria e genera enormi stringhe memorizzate nella cache, il che causa problemi a determinate pagine con molti script e stili inseriti dinamicamente nella whitelist. La patch fornita ottimizza questo processo. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19. L'ID della patch è MDVA-31307. Tieni presente che il problema è risolto in Adobe Commerce 2.4.2.
exl-id: 15d82f5b-bd43-4a0a-b756-d109dac6d2cd
feature: Cache, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-31307: memoria insufficiente in alcune categorie

La patch di MDVA-31307 risolve il problema relativo al fatto che `Magento\_Csp/Model/BlockCache` consuma molta memoria e genera stringhe memorizzate nella cache di grandi dimensioni, causando problemi ad alcune pagine con molti script e stili inseriti nella whitelist in modo dinamico. La patch fornita ottimizza questo processo. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19. L&#39;ID della patch è MDVA-31307. Tieni presente che il problema è risolto in Adobe Commerce 2.4.2.

## Prodotti e versioni interessati

**La patch è stata creata per Adobe Commerce versione:** Adobe Commerce su infrastruttura cloud 2.4.0

**Compatibile con le versioni di Adobe Commerce:** Adobe Commerce on-premise e Adobe Commerce on cloud infrastructure 2.4.0 - 2.4.1-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

È stato risolto il problema relativo a *memoria insufficiente* errori in alcune categorie a causa di problemi con l&#39;inserimento di CSP dinamici nella whitelist per i blocchi memorizzati nella cache.

<u>Passaggi da riprodurre:</u>

1. Generare piccoli elementi di fissaggio del profilo (`bin/magento setup:performance:generate-fixtures`).
1. Apri tutte le pagine delle categorie in schede diverse.

<u>Risultato effettivo:</u>

*[data e ora] Errore irreversibile PHP: memoria consentita di 1073741824 byte esaurita (tentativo di allocare 90112 byte) in Sconosciuto alla riga 0
[data e ora] Errore irreversibile PHP: memoria consentita di 1073741824 byte esaurita (tentativo di allocare 33554440 byte) in /app/`<project-id>`/vendor/magento/module-csp/Model/Collector/DynamicCollector.php alla riga 31*

<u>Risultato previsto:</u>

Tutte le pagine sono state aperte correttamente.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
