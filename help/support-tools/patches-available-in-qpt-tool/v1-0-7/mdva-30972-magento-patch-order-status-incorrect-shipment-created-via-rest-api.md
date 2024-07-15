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

La patch MDVA-30972 risolve il problema relativo alla modifica non corretta dello stato dell&#39;ordine durante la creazione della spedizione tramite l&#39;API REST. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce sull’infrastruttura cloud 2.3.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) da 2.3.0 a 2.4.2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando viene creata una spedizione parziale dall&#39;amministratore tramite API REST per un ordine con *Stato sospetto frode*, lo stato dell&#39;ordine viene modificato in *Elaborazione*. Deve rimanere in *Sospetta frode*.

<u>Prerequisiti</u>:

* PayPal EC o un altro metodo di pagamento online è impostato.
* È stata impostata l’integrazione per l’API REST.

<u>Passaggi da riprodurre</u>:

1. Crea un ordine con due o più elementi.
1. Accedi a **Amministratore** > **Vendite** > **Ordini**. Apri l’ordine appena creato.
1. Nella pagina dei dettagli dell&#39;ordine, scorri verso il basso fino a **Totale ordine**. Fai clic sul menu a discesa **Stato** e seleziona *Sospetta frode*. Quindi fare clic sul pulsante **Invia commento**.
1. Verifica che l&#39;ordine sia ora in stato *Sospetta frode*.
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

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
