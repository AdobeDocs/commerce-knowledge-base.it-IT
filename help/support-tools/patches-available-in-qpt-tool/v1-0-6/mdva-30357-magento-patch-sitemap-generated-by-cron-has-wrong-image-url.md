---
title: "MDVA-30357: l'URL dell'immagine della mappa del sito generata da cron non è corretto"
description: La patch MDVA-30357 risolve il problema relativo alla creazione di un URL immagine errato da parte di una sitemap generata da cron in Commerce Admin. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6. Il problema è stato risolto in Adobe Commerce 2.4.2.
exl-id: c91f7ae0-0970-4918-9d1f-4ede6bfcb05f
feature: Marketing Tools
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 0%

---

# MDVA-30357: URL immagine errato per la mappa del sito generata da cron

La patch MDVA-30357 risolve il problema relativo alla creazione di un URL immagine errato da parte di una sitemap generata da cron in Commerce Admin. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6. Il problema è stato risolto in Adobe Commerce 2.4.2.

## Prodotti e versioni interessati

* Adobe Commerce (tutti i metodi di implementazione) da 2.3.2 a 2.4.0

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le mappe del sito generate da cron in Adobe Commerce contengono il percorso URL dell’immagine errato.

<u>Passaggi da riprodurre</u>:

1. Nell’amministratore di Commerce, crea una nuova visualizzazione per siti web, store o store.
1. Aggiungi almeno un prodotto a ciascun negozio e aggiungi almeno un&#39;immagine a ciascun prodotto.
1. Abilita **Generazione mappa del sito in base alla pianificazione** in **Amministratore** > **Archivi** > **Configurazione** > **CATALOGO** > **Mappa del sito XML** > **Impostazioni di generazione**.
1. Genera manualmente una mappa del sito per uno qualsiasi dei due archivi in **Admin** > **Marketing** > **Mappa del sito** utilizzando un nome di mappa del sito come &quot;*sitemap.xml*&quot;.
   * Rinomina il file in un formato simile a &quot;*manual\_sitemap.xml*&quot; o copia il contenuto del file in un editor di testo.
1. Generare la stessa mappa del sito con il processo cron `sitemap_generate`.
1. Confronta la mappa del sito generata manualmente &quot;*manual\_sitemap.xml*&quot; e la mappa del sito generata da cron &quot;*sitemap.xml*&quot;.

<u>Risultati previsti</u>:

L’URL del percorso dell’immagine della sitemap memorizzata nella cache è corretto.

<u>Risultati effettivi</u>:

La mappa del sito generata da cron contiene l’URL del percorso immagine errato. Se tenti di aprire l&#39;immagine da &quot;*sitemap.xml*&quot;, verrà visualizzato un segnaposto predefinito. Questo problema non influisce sugli URL di sitemap generati manualmente.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.

Per ulteriori informazioni sulle sitemap, consulta questi articoli nella documentazione per gli sviluppatori:

* [Aggiungi mappa del sito e robot motore di ricerca](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html)
* [Configurare ed eseguire cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html)
* [Cron.php protetto da eseguire in un browser](https://devdocs.magento.com/guides/v2.4/config-guide/secy/secy-cron.html)
