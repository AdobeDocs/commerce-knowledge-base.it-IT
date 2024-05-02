---
title: "MDVA-37478: impossibile creare una fattura parziale tramite API REST"
description: La patch MDVA-37478 risolve il problema quando non è possibile creare una fattura parziale tramite API REST per un ordine effettuato con il metodo di pagamento **Pagamento in acconto**. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23. L'ID della patch è MDVA-37478. Il problema è pianificato per la risoluzione in Adobe Commerce versione 2.4.3.
exl-id: 1b235baa-a188-467c-8ae5-de0836bc2caa
feature: REST, B2B, Invoices
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# MDVA-37478: impossibile creare una fattura parziale tramite API REST

La patch MDVA-37478 risolve il problema quando non è possibile creare una fattura parziale tramite API REST per un ordine effettuato con metodo di pagamento **Pagamento in acconto**. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23. L&#39;ID della patch è MDVA-37478. Il problema è pianificato per la risoluzione in Adobe Commerce versione 2.4.3.

## Prodotti e versioni interessati

* La patch è stata progettata per Adobe Commerce sull’infrastruttura cloud 2.3.3-p1
* La patch è compatibile anche con Adobe Commerce on-premise e Adobe Commerce on cloud infrastructure 2.3.0-2.3.7

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Prerequisito</u>:

Adobe Commerce con modulo B2B installato

<u>Passaggi da riprodurre</u>:

1. Abilita **Società B2B**.
1. Abilita **Pagamento in acconto** metodo di pagamento.
1. Crea 2 prodotti semplici.
1. Crea un account aziendale.
1. Aggiungi i crediti aziendali che superano il prezzo totale di 2 prodotti creati.
1. Accedi al front-end utilizzando l’account aziendale creato.
1. Aggiungi i 2 prodotti creati al carrello ed effettua il pagamento utilizzando **Pagamento in acconto** metodo di pagamento.
1. Prova a creare una fattura parziale per l’ordine creato tramite API REST:

   ```php
   POST /rest/V1/order//invoice
   {
     "items": [
       {
         "order_item_id": 2,
         "qty": 1
       }
     ]
   }
   ```

<u>Risultati previsti</u>:

La fattura parziale viene creata per un ordine effettuato utilizzando **Pagamento in acconto** metodo di pagamento, come previsto.

<u>Risultati effettivi</u>:

Dall’API REST viene restituito il seguente errore:

```php
{"message":"Invoice Document Validation Error(s):\nAn invoice for partial quantities cannot be issued for this order. To continue, change the specified quantity to the full quantity."}
```

## Applicare la patch

Per applicare singole patch, utilizzare i seguenti collegamenti, a seconda del prodotto Adobe Commerce:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili nello strumento QPT, consultare [Patch disponibili nello strumento QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sezione.
