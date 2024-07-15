---
title: "MDVA-34189: il merchandiser visivo esegue query MySQL lunghe"
description: La patch MDVA-34189 risolve il problema relativo all'esecuzione da parte di Adobe Commerce di query di grandi dimensioni su Visual Merchandiser durante il caricamento della pagina della categoria Admin.
exl-id: 94143d80-3240-4a18-890d-fb759ea9c30d
feature: Categories, Merchandising, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# MDVA-34189: Visual merchandiser esegue query MySQL lunghe

La patch MDVA-34189 risolve il problema relativo all&#39;esecuzione da parte di Adobe Commerce di query di grandi dimensioni su Visual Merchandiser durante il caricamento della pagina della categoria Admin.

Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18. L&#39;ID della patch è MDVA-34189. Il problema è pianificato per la risoluzione in Adobe Commerce versione 2.4.3.

## Prodotti e versioni interessati

**La patch è stata creata per Adobe Commerce versione:** Adobe Commerce su infrastruttura cloud 2.3.5-p2

**Compatibile con le versioni di Adobe Commerce:** Adobe Commerce on-premise e Adobe Commerce on cloud infrastructure 2.3.4-2.4.2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il sito Web esegue query MySQL di grandi dimensioni sul server di produzione.

<u>Passaggi da riprodurre</u>:

1. Per accedere a Visual Merchandiser vai alla barra laterale *Admin*, fai clic su **Catalogo** > **Categorie**.
1. Carica la pagina **Categorie** nel pannello di amministrazione (caricamento iniziale della categoria principale) e osserva le query eseguite.

<u>Risultato previsto</u>:

La pagina Amministratore **Categorie** deve essere caricata senza generare query lente.

<u>Risultato effettivo</u>:

Questo dipende dalla configurazione PHP. L&#39;esempio più comune di questo errore è che la pagina **Categories** non si apre e viene visualizzato un errore *Errore 503, primo byte di timeout*.

In alternativa, quando Adobe Commerce carica Visual Merchandiser, esegue una query MySQL lenta. Questa query include molti ID prodotto inseriti in `ORDER BY FIELD(`e`.`entity_id`,  ...)`

in `app/code/Magento/VisualMerchandiser/Model/Category/Products.php:: applyPositions`

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili nello strumento QPT, fare riferimento alla sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
