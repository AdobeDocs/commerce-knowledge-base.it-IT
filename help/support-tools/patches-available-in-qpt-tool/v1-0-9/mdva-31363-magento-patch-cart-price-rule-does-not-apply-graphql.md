---
title: "Patch MDVA-31363: la regola del prezzo del carrello non è applicabile (GraphQL)"
description: La patch MDVA-31363 risolve il problema per cui la regola del prezzo del carrello con coupon non viene applicata tramite GraphQL quando viene utilizzata l'azione 'Sconto importo fisso per carrello intero'. Questa patch è disponibile quando è installato QPT 1.0.9. Il problema è pianificato per essere risolto nella versione 2.4.2 di Adobe Commerce.
exl-id: f64fbbb1-b5fd-4624-bcdd-d1e6c1f9acfe
feature: GraphQL, Orders, Price Rules, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# Patch MDVA-31363: la regola del prezzo del carrello non è applicabile (GraphQL)

>[!WARNING]
>
>Una nuova patch denominata MDVA-33975 risolve i problemi di calcolo dei prezzi di GraphQL. MDVA-31363 è obsoleto e si consiglia di applicare la patch MDVA-33975. Per accedere a questa patch, fare riferimento a [Patch MDVA-33975: calcolo dei prezzi GraphQL](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/mdva-33975-magento-patch-graphql-price-calculations.html).

La patch MDVA-31363 risolve il problema per cui la regola del prezzo del carrello con coupon non viene applicata tramite GraphQL quando viene utilizzata l&#39;azione &#39;Sconto importo fisso per carrello intero&#39;. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9. Il problema è pianificato per essere risolto nella versione 2.4.2 di Adobe Commerce.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.4.0

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud e Adobe Commerce on-premise 2.3.2 - 2.4.1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il ricalcolo dei totali delle offerte prima di fornire una risposta sui prezzi delle offerte causa la perdita delle regole applicate.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto semplice.
1. Crea una regola di prezzo del carrello con uno sconto di importo fisso per l&#39;intero carrello.
1. Crea un nuovo carrello con GraphQL.
1. Salva la scheda\_id dalla risposta e aggiungi il prodotto dal passaggio 1 al carrello utilizzando GraphQL.
1. Attiva la regola del prezzo del carrello aggiungendo il codice del coupon al carrello utilizzando GraphQL.
1. Controlla il prezzo nella risposta.

<u>Risultati previsti</u>:

Viene applicato uno sconto.

<u>Risultati effettivi</u>:

Sconto non applicato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
