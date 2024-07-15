---
title: "MDVA-38929: la fattura con FPT mostra un totale errato"
description: La patch MDVA-38929 risolve il problema che la fattura con FPT presenta un totale complessivo errato quando l'ordine viene pagato con il credito del negozio. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2. L'ID della patch è MDVA-38929. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
exl-id: 1ed0e311-f4a5-4dc0-98fc-fc1cc9458516
feature: Invoices, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# MDVA-38929: la fattura con FPT mostra un totale errato

La patch MDVA-38929 risolve il problema che la fattura con FPT presenta un totale complessivo errato quando l&#39;ordine viene pagato con il credito del negozio. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2. L&#39;ID della patch è MDVA-38929. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La fattura con FPT mostra un totale complessivo errato quando l&#39;ordine viene pagato con il credito del negozio.

<u>Passaggi da riprodurre</u>:

1. Creare un cliente e assicurarsi che il cliente disponga di credito di punto vendita sufficiente per coprire l&#39;ordine.
1. Abilitare FPT e aggiungere FPT a un prodotto.
1. Dal front-end, accedi come il cliente ha appena creato.
1. Aggiungi il prodotto con FPT al carrello.
1. Pagare con il credito del negozio. Dovrebbe essere un ordine di paga pari a zero.
1. Passare a Ordini e fatturare manualmente l&#39;ordine.
1. Controllare il totale complessivo della fattura.

<u>Risultati previsti</u>:

* Il totale complessivo della fattura è zero.
* L&#39;importo totale pagato dell&#39;ordine è zero.

<u>Risultati effettivi</u>:

* Il totale complessivo della fattura mostra ancora l&#39;importo FPT.
* Il totale pagato mostra ancora l&#39;importo FPT.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
