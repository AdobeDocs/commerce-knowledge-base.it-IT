---
title: "MDVA-37916: PayPal Payments Advanced non ritorna alla pagina di conferma"
description: La patch di qualità MDVA-37916 per Adobe Commerce risolve il problema che PayPal Payments Advanced non ritorni alla pagina di conferma dopo il pagamento. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25. L'ID della patch è MDVA-37916. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
exl-id: 18d7bb1c-d73a-43f6-90a8-650290dfd114
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# MDVA-37916: PayPal Payments Advanced non ritorna alla pagina di conferma

La patch di qualità MDVA-37916 per Adobe Commerce risolve il problema che PayPal Payments Advanced non ritorni alla pagina di conferma dopo il pagamento. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25. L&#39;ID della patch è MDVA-37916. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**
Adobe Commerce sull’infrastruttura cloud 2.3.6-p1

**Compatibile con le versioni di Adobe Commerce:**
Adobe Commerce on-premise e Adobe Commerce sull’infrastruttura cloud 2.3.6-2.4.2-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il cliente non viene reindirizzato alla pagina Conferma pagamento dopo il pagamento quando si utilizza il metodo PayPal Payments Advanced.

<u>Passaggi da riprodurre</u>: [Screencast](https://assets.adobe.com/public/025d479b-5796-4772-6f3d-adc86306a799)

1. Aggiungi il prodotto al carrello e passa alla fase di pagamento della pagina di pagamento.
1. Seleziona **Carta di credito (Payflow Advanced)** opzione di pagamento.
1. Clic **Continua** per visualizzare l’iframe con il modulo di pagamento.
1. Compila il modulo di pagamento con i dettagli della carta di credito sandbox.
   * Numero di carta: 4444 3333 2222 1111 o 4111 1111 111 111 111
   * Data di scadenza: 23/12
   * CSC: 123
1. Clic **Paga ora**.

<u>Risultati previsti</u>:

Dopo aver elaborato il pagamento e averlo eseguito correttamente, si viene reindirizzati alla pagina Conferma ordine.

<u>Risultati effettivi</u>:

* NON viene effettuato il reindirizzamento alla pagina Conferma ordine.
* Ma l’ordine è stato creato in Adobe Commerce.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce on-premise: [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html)

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità nella nostra knowledge base di supporto, consulta:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

Per informazioni sulle altre patch disponibili nello strumento QPT, consultare [Patch disponibili nello strumento QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) nella knowledge base di supporto.
