---
title: "Patch MDVA-31399: Subtotale (incl. Imposta) nella condizione della regola del carrello"
description: La patch MDVA-31399 aggiunge il *Subtotale (incl. Imposta)* opzione per [condizione regola prezzo carrello](https://docs.magento.com/user-guide/v2.3/marketing/price-rules-cart-create.html#step-2-describe-the-conditions), che fissa il problema relativo all’impossibilità di applicare una regola prezzo carrello basata sul subtotale (incl. Partita IVA. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12.
exl-id: ea0f4060-753a-4b0d-896b-fff54ffd1a82
feature: Marketing Tools, Orders, Shopping Cart, Taxes
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# Patch MDVA-31399: Subtotale (incl. Imposta) nella condizione della regola carrello

La patch MDVA-31399 aggiunge *Subtotale (Incl. Imposta)* opzione per [condizione regola prezzo carrello](https://docs.magento.com/user-guide/v2.3/marketing/price-rules-cart-create.html#step-2-describe-the-conditions), per risolvere il problema relativo all&#39;impossibilità di applicare una regola del prezzo del carrello basata sul subtotale (incl. Partita IVA. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.5-p2

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud e Adobe Commerce on-premise 2.3.2 - 2.4.1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

È impossibile applicare una regola di prezzo del carrello basata sul subtotale (incl. Partita IVA.

<u>Passaggi da riprodurre</u>:

1. Configura il prezzo del prodotto in modo da includere l&#39;imposta.
1. Creare una regola fiscale e un&#39;aliquota per il 20%.
1. Creare un prodotto con **Prezzo** = *100* (questo prezzo include le imposte).
1. Crea una nuova regola di prezzo del carrello con un coupon &quot;10off&quot; per applicare uno sconto fisso di $ 10 se il subtotale corrisponde a queste condizioni:

**Condizioni**: *Se TUTTE queste condizioni sono TRUE:*        * **Subtotale** è uguale o maggiore di 100.*

<u>Risultati previsti</u>:

È possibile creare una regola di prezzo del carrello del subtotale con il coupon per applicare lo sconto al subtotale, imposte incluse.

<u>Risultati effettivi</u>:

Nelle condizioni delle regole del carrello sono disponibili due opzioni: *Subtotale* e *Subtotale (escl. Imposta)*, e qualsiasi sia selezionato, la regola viene applicata solo al subtotale escluse le imposte.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
