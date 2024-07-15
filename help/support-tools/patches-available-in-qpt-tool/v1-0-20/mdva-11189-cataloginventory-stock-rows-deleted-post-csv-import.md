---
title: "MDVA-11189: righe cataloginventory_stock eliminate dopo l’importazione CSV"
description: La patch di MDVA-11189 Adobe Commerce risolve il problema quando, dopo aver importato un file .csv per aggiornare le scorte di prodotto, le righe della tabella "cataloginventory_stock" vengono eliminate. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20. L'ID della patch è MDVA-1189. Il problema è stato risolto in Adobe Commerce 2.3.5.
exl-id: 84e1979c-826c-4c01-b0c7-8054bb4b23f0
feature: Catalog Management, Data Import/Export, Inventory, Orders
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 0%

---

# MDVA-11189: righe cataloginventory_stock eliminate dopo l’importazione CSV

La patch di MDVA-11189 Adobe Commerce risolve il problema quando, dopo aver importato un file .csv per aggiornare il materiale di partenza, le righe della tabella `cataloginventory_stock` vengono eliminate. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20. L&#39;ID della patch è MDVA-1189. Il problema è stato risolto in Adobe Commerce 2.3.5.

## Prodotti e versioni interessati

**La patch è stata creata per Adobe Commerce versione:** Adobe Commerce sull&#39;infrastruttura cloud 2.2.3

**Compatibile con le versioni di Adobe Commerce:** Adobe Commerce (tutti i metodi di distribuzione) 2.3.0-2.3.4-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

È stato risolto il problema che si verificava quando, dopo l&#39;importazione di un `.csv` per l&#39;aggiornamento delle scorte di prodotto, le righe della tabella `cataloginventory_stock` venivano eliminate.

<u>Passaggi da riprodurre:</u>

1. Nel database eseguire il comando MySQL seguente: `select count(*) from cataloginventory_stock_status;`
1. Prendi nota del numero di righe.
1. Impostare la scheda cronologica come segue: `* * * * * /usr/bin/php <path to installation>/bin/magento cron:run  | grep -v "Ran jobs by schedule" >> <path to installation>/var/log/cron.log 2>&1`
1. Vai al pannello di amministrazione in **Sistema** > **Strumenti** > **Gestione indice**.
1. Imposta gli indicizzatori su *Aggiorna per pianificazione.*
1. Vai a **Sistema** > *Trasferimento dati* > **Esporta**.
1. Imposta **Tipo di entità** uguale a *Prodotti* > **Continua**.
1. Apri il file `.csv` salvato > Rimuovi tutte le colonne ad eccezione di SKU e QTY.
1. Aggiorna a 150 la quantità per tutti i prodotti.
1. Salva il file `.csv`.
1. Vai a **Sistema** > *Trasferimento dati* > **Importa** .
1. Imposta i seguenti valori:
   1. Tipo di entità: *Prodotti*
   1. Comportamento importazione: *Aggiungi/Aggiorna*
   1. Lascia tutti gli altri valori come predefiniti.
   1. Scegliere File per selezionare il foglio di calcolo del prodotto del catalogo.
1. Fai clic su **Verifica dati** > **Importa**. Attendere 5-10 minuti.
1. Nel database eseguire il comando MySQL seguente:
   `select count(*) from cataloginventory_stock_status;`

<u>Risultato effettivo:</u>

Il numero di righe in `cataloginventory_stock` viene diminuito dopo l&#39;importazione del file CSV per aggiornare il materiale.

<u>Risultato previsto:</u>

Il numero di righe in `cataloginventory_stock` deve rimanere invariato dopo l&#39;importazione del file CSV per aggiornare il materiale.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
