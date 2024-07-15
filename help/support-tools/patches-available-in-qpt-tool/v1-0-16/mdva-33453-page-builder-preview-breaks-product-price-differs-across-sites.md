---
title: "MDVA-33453: l’anteprima di Page Builder interrompe il prezzo del prodotto, ma differisce tra i siti"
description: La patch MDVA-33453 risolve il problema relativo all'interruzione dell'anteprima di Page Builder se i prodotti corrispondenti hanno un prezzo diverso per ogni sito Web. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.3.
exl-id: 78a7f7d4-8691-4b5d-a900-1c9a6ec73486
feature: CMS, Orders, Page Builder, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# MDVA-33453: l&#39;anteprima di Page Builder interrompe il prezzo del prodotto e differisce tra i siti

La patch MDVA-33453 risolve il problema relativo all&#39;interruzione dell&#39;anteprima di Page Builder se i prodotti corrispondenti hanno un prezzo diverso per ogni sito Web. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch è stata creata per Adobe Commerce versione:** Adobe Commerce sull&#39;infrastruttura cloud 2.4.1

**Compatibile con le versioni di Adobe Commerce:** Adobe Commerce su infrastruttura cloud e Adobe Commerce on-premise 2.3.6 - 2.4.1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’anteprima del prodotto Page Builder si interrompe quando è presente un prodotto con prezzi diversi su siti web diversi.

<u>Passaggi da riprodurre</u>:

1. Accedi al pannello di amministrazione di Commerce.
1. Crea due siti Web.
1. Crea un prodotto semplice.
1. Imposta un prezzo diverso per il prodotto su ciascun sito Web.
1. Esegui cron e reindicizza.
1. Crea o modifica una pagina CMS e utilizza il blocco di prodotto per aggiungere il prodotto.

<u>Risultato effettivo</u>:<br>

Si verifica l’errore seguente:

*Errore nel filtraggio del modello: esiste già un elemento (Magento\\Catalog\\Model\\Product\\Interceptor) con lo stesso ID &quot;2&quot;.*

<u>Risultato previsto</u>:<br>

Non viene visualizzato alcun errore.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta le [patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
