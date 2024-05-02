---
title: "MDVA-36138: regola di spedizione gratuita non applicata al carrello più articoli"
description: La patch MDVA-36138 risolve il problema che, quando nel carrello sono presenti più articoli, lo SKU corrispondente nella Spedizione gratuita non riceve la spedizione gratuita applicata. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21. L'ID della patch è MDVA-36138. Il problema è stato risolto in Adobe Commerce 2.4.3.
exl-id: 74e25ca8-e4fa-47f4-ab95-561f70e05727
feature: Orders, Shipping/Delivery, Personalization, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# MDVA-36138: regola di spedizione gratuita non applicata al carrello più articoli

La patch MDVA-36138 risolve il problema che, quando nel carrello sono presenti più articoli, lo SKU corrispondente nella Spedizione gratuita non riceve la spedizione gratuita applicata. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21. L&#39;ID della patch è MDVA-36138. Il problema è stato risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.4

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.2 e versioni successive

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Se una regola di spedizione gratuita viene applicata solo ad articoli specifici, lo sconto non viene applicato quando nel carrello sono presenti altri articoli.

<u>Passaggi da riprodurre</u>:

1. Creare prodotti semplici: simple1 e simple2.
1. Configura USPS (o qualsiasi metodo di spedizione online):

   * Metodi consentiti: posta prioritaria (un metodo selezionato al fine di non avere un lungo elenco di metodi nel carrello e nel pagamento).
   * Metodo libero: posta prioritaria.

1. Crea una regola del carrello:

   * Specifica il codice coupon
   * Scheda Condizioni: lascia vuoto
   * Scheda Azioni:

   `Condition: SKU is simple1`
   `Free Shipping: For matching items only`

1. Aggiungi simple1 al carrello.
1. Applica il codice del coupon.
1. Aggiungi simple2 al carrello.

<u>Risultati previsti</u>:

* simple1 - deve avere spedizione gratuita.
* simple2 - la spedizione deve essere pagata.

<u>Risultati effettivi</u>:

Il prezzo di spedizione include simple1 e simple2.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
