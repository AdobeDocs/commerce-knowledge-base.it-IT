---
title: "Patch MDVA-33975: calcolo dei prezzi GraphQL"
description: "La patch MDVA-33975 risolve alcuni problemi di calcolo dei prezzi di GraphQL. Tali problemi includono:"
exl-id: a8266334-72cb-4b50-9ff5-9a977d762e5c
feature: GraphQL, Customer Service, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Patch MDVA-33975: calcolo dei prezzi GraphQL

La patch MDVA-33975 risolve i problemi di calcolo dei prezzi di GraphQL. Tali problemi includono:

* Quando una regola del prezzo di catalogo viene applicata a un determinato gruppo di clienti, i prezzi degli articoli nel carrello e il totale dell’ordine non vengono calcolati correttamente in GraphQL.
* Le regole di prezzo del catalogo non sono incluse in `CartItemPrices` nell’API.
* Il prezzo di gruppo del cliente per il cliente generico non viene aggiunto nella risposta alla query del prodotto GraphQL.
* Il ricalcolo dei totali delle offerte prima di fornire una risposta sui prezzi delle offerte causa la perdita delle regole applicate.
* Lo sconto sull&#39;importo della spedizione non è stato recuperato nell&#39;ultima fase di fatturazione e il totale complessivo non è stato visualizzato correttamente.
* Lo sconto non viene applicato in GraphQL quando il segmento del cliente viene utilizzato nella condizione della regola del prezzo del carrello.

Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.14.

## Prodotti e versioni interessati

* La patch è stata progettata per Adobe Commerce on-premise 2.4.1.
* La patch è compatibile anche con le seguenti versioni di Adobe Commerce: Adobe Commerce on-premise e Adobe Commerce on cloud infrastructure 2.3.4 - 2.4.1.

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Applicare la patch

Per applicare singole patch, utilizzare i seguenti collegamenti, a seconda del prodotto Adobe Commerce:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili nello strumento QPT, consultare [Patch disponibili nello strumento QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sezione.
