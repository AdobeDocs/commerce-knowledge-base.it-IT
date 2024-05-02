---
title: "MDVA-30972: spedizione non corretta dello stato dell’ordine creata tramite API REST"
description: La patch MDVA-30972 risolve il problema relativo alla modifica non corretta dello stato dell'ordine durante la creazione della spedizione tramite l'API REST. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7.
exl-id: 70b8db1f-16d0-48f4-b0a2-483a7176cb89
feature: REST, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# MDVA-30972: spedizione non corretta dello stato dell&#39;ordine creata tramite API REST

La patch MDVA-30972 risolve il problema relativo alla modifica non corretta dello stato dell&#39;ordine durante la creazione della spedizione tramite l&#39;API REST. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce sull’infrastruttura cloud 2.3.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) da 2.3.0 a 2.4.2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando viene creata una spedizione parziale dall’amministratore tramite API REST per un ordine con *Sospetta frode* stato dell’ordine, lo stato dell’ordine viene modificato in *Elaborazione*. Dovrebbe rimanere al *Sospetta frode*.

<u>Prerequisiti</u>:

* PayPal EC o un altro metodo di pagamento online è impostato.
* È stata impostata l’integrazione per l’API REST.

<u>Passaggi da riprodurre</u>:

1. Crea un ordine con due o più elementi.
1. Accedi a **Amministratore** > **Vendite** > **Ordini**. Apri l’ordine appena creato.
1. Nella pagina dei dettagli dell’ordine, scorri verso il basso fino a **Totale ordine**. Fai clic sul pulsante **Stato** a discesa e selezionare *Sospetta frode*. Quindi fai clic su **Invia commento** pulsante.
1. Verifica che l’ordine abbia *Sospetta frode* ora lo stato.
1. Crea una spedizione per un articolo dall’ordine utilizzando l’API REST:

   ```
   * Method = `Post`
   * Header = `"{host}/rest/V1/orders/ {order_id}/ship"`
   * Body =
   ```

   ```
    {      "items": [        {          "extension_attributes": {},          "order_item_id": {order_item_id},          "qty": 1        }      ]    }
   ```

1. Apri nuovamente l’ordine in Amministratore e controllane lo stato.

<u>Risultati previsti</u>:

* Stato ordine = *Sospetta frode*.
* Lo stato dell&#39;ordine non viene modificato se la stessa spedizione viene creata dall&#39;amministratore.

<u>Risultati effettivi</u>:

Stato ordine = *Elaborazione*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
