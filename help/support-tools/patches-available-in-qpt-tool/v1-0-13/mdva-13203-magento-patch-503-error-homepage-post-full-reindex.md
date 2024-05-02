---
title: "Patch MDVA-13203: errore 503 nella home page dopo la reindicizzazione completa"
description: '"La patch di MDVA-13203 Adobe Commerce risolve il problema relativo alla visualizzazione di una pagina di manutenzione e agli errori *CRITICO: SQLSTATE\[23000\]: Violazione del vincolo di integrità* in "system.log". L''ID della patch è MDVA-13203. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13.'
exl-id: 8e09010b-9aa4-4a79-b546-a24bb72e0e40
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# Patch MDVA-13203: errore 503 nella home page dopo la reindicizzazione completa

La patch di MDVA-13203 Adobe Commerce risolve il problema relativo alla visualizzazione di una pagina di manutenzione nel sito *CRITICO: SQLSTATE\[23000\]: violazione vincolo di integrità* errori in `system.log`. L&#39;ID della patch è MDVA-13203. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:** Adobe Commerce sull’infrastruttura cloud 2.2.4.

**Compatibile con le versioni di Adobe Commerce:** Adobe Commerce (tutti i metodi di implementazione) 2.3.0-2.4.1.

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Passaggi da riprodurre:</u>

1. Passa all’URL interessato.
1. Viene visualizzata la pagina di manutenzione.
1. Verifica che il sito non sia in stato di manutenzione tramite SSH:
   <pre> bin/magento maintenance:status: modalità di manutenzione non attiva Elenco di indirizzi IP esenti: nessuno</pre>
1. Osserva `system.log`:

<pre>grep critical -i var/log/system.log |tail [2018-09-04 17]:05:18] report.CRITICAL: SQLSTATE[23000]: violazione del vincolo di integrità: 1062 Voce duplicata '4613' per la chiave 'PRIMARY'. Query: INSERT INTO 'search_tmp_5b8ebb4e994da5_88027289' (`entity_id`,`score`) VALUES (?, ?),... (?, ?), (?, ?) [] [] [2018-09-04 17]:05:21] report.CRITICAL: SQLSTATE[23000]: violazione del vincolo di integrità: 1062 Voce duplicata "4613" per la chiave "PRIMARY". Query: INSERT INTO "search_tmp_5b8ebb51579943_52333638" ("entity_id", "score") VALORI (?, ?),...,(?, ?) [] [] [2018-09-04 17]:05:47] report.CRITICAL: SQLSTATE[23000]: violazione del vincolo di integrità: 1062 Voce duplicata '1350' per la chiave 'PRIMARY', query: INSERT INTO 'search_tmp_5b8ebb6b7028f4_68065024' (`entity_id`,`score`) VALUES (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?) (?, ?), (?, ?), (?, ?), (?, ?) [] [] [2018-09-04 17]:05:47] report.CRITICAL: SQLSTATE[23000]: violazione del vincolo di integrità: 1062 Voce duplicata '1350' per la chiave 'PRIMARY', query: INSERT INTO 'search_tmp_5b8ebb6b7885a9_23360993' (`entity_id`,`score`) VALUES (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?) (?, ?), (?, ?), (?, ?), (?, ?) [] [] data mar 4 set 17:06:11 UTC 2018</pre>

<u>Risultati previsti:</u> Dovresti vedere il sito.

<u>Risultati effettivi:</u> La pagina di manutenzione viene visualizzata a causa di problemi di coerenza del database.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
