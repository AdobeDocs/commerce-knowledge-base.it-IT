---
title: "MDVA-39229: errore dopo l'aggiornamento dell'ora di inizio dell'aggiornamento della gestione temporanea della regola del catalogo"
description: La patch di MDVA-39229 risolve il problema relativo all'errore restituito dagli utenti dopo l'aggiornamento dell'ora di inizio dell'aggiornamento della gestione temporanea delle regole del catalogo. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.5. L'ID della patch è MDVA-39229. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
exl-id: b9a203af-693d-4253-877b-591ae5f388d3
feature: Catalog Management, Staging
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# MDVA-39229: errore dopo l&#39;aggiornamento dell&#39;ora di inizio dell&#39;aggiornamento della gestione temporanea della regola del catalogo

La patch di MDVA-39229 risolve il problema relativo all&#39;errore restituito dagli utenti dopo l&#39;aggiornamento dell&#39;ora di inizio dell&#39;aggiornamento della gestione temporanea delle regole del catalogo. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.5. L&#39;ID della patch è MDVA-39229. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.4-p2

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli utenti ricevono un errore dopo l’aggiornamento dell’ora di inizio dell’aggiornamento della gestione temporanea della regola del catalogo.

<u>Passaggi da riprodurre</u>:

1. Crea una regola di prezzo catalogo.
1. Crea ed esegui qualsiasi aggiornamento di staging.
1. Esegui la query e verifica che il flag Staging sia stato creato.


   `select * from flag;`


1. Crea un nuovo aggiornamento di staging da avviare dopo cinque minuti.
1. Apri **Contenuto** > **Staging** > **Dashboard** > **Nuovo aggiornamento** e ritardare di un minuto l&#39;ora di inizio.
1. Aspettate sei minuti.
1. Esegui cron.

<u>Risultati previsti</u>:

L&#39;ora di inizio dell&#39;aggiornamento viene modificata e l&#39;aggiornamento viene applicato. Il vecchio aggiornamento viene eliminato da `staging_update` tabella.

<u>Risultati effettivi</u>:

Gli utenti ricevono il seguente errore:

*report.ERROR: Errore del processo di replica staging_synchronize_entities_period: impossibile eliminare l&#39;aggiornamento attivo.*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sezione.
