---
title: "MDVA-43451: errore durante l'impostazione di prezzi e struttura per il catalogo condiviso"
description: La patch MDVA-43451 risolve il problema che impedisce all'utente di impostare i prezzi e la struttura per un catalogo condiviso. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13. L'ID della patch è MDVA-43451. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: 78de2e98-dfd7-4829-8e3f-76eadf5570e8
feature: Catalog Management
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# MDVA-43451: errore durante l&#39;impostazione di determinazione prezzi e struttura per il catalogo condiviso

La patch MDVA-43451 risolve il problema che impedisce all&#39;utente di impostare i prezzi e la struttura per un catalogo condiviso. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13. L&#39;ID della patch è MDVA-43451. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;utente non è in grado di impostare i prezzi e la struttura per un catalogo condiviso. Viene visualizzato il seguente messaggio: *Impossibile trovare l&#39;archivio richiesto. Verifica l’archivio e riprova.*

<u>Passaggi da riprodurre</u>:

1. Crea un sito web personalizzato. Gli ID dei siti Web devono essere 0, 1, 2.
1. Crea un Negozio nel sito Web sopra riportato. Gli ID dei negozi devono essere 0,1,2.
1. Crea tre visualizzazioni store per lo store precedente. Gli ID delle visualizzazioni dello store devono essere 0, 1, 2, 3, 4.
1. Elimina la visualizzazione store con ID 2. Ora il tavolo del negozio dovrebbe assomigliare al seguente tabella.

   ```bash
   MariaDB [m24devinvb2b]> SELECT store_id,code,website_id,group_id,name FROM store;
   +----------+----------------+------------+----------+--------------------+
   | store_id | code           | website_id | group_id | name               |
   +----------+----------------+------------+----------+--------------------+
   |        0 | admin          |          0 |        0 | Admin              |
   |        1 | default        |          1 |        1 | Default Store View |
   |        3 | web1storeview2 |          2 |        2 | web1storeview2     |
   |        4 | web1storeview3 |          2 |        2 | web1storeview3     |
   +----------+----------------+------------+----------+--------------------+
   ```

1. Crea un nuovo catalogo condiviso.
1. Durante la configurazione di Prezzo e struttura, selezionare il negozio creato nel passaggio 2.
1. Salva il catalogo condiviso.

<u>Risultati previsti</u>:

Il catalogo condiviso viene salvato senza alcun problema.

<u>Risultati effettivi</u>:

Impossibile salvare il catalogo condiviso. Viene visualizzato il seguente errore:
*Impossibile trovare l&#39;archivio richiesto. Verifica l’archivio e riprova.*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
