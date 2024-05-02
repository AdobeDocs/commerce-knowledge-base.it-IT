---
title: 'MDVA-37224: impossibile pagare un "preventivo negoziabile" con PayFlow Pro'
description: La patch MDVA-37224 risolve il problema quando i clienti non sono in grado di pagare un **Offerta negoziabile** con Paypal PayFlow Pro. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23. L'ID della patch è MDVA-37224. Il problema è pianificato per la risoluzione in Adobe Commerce versione 2.4.3.
exl-id: df75b38d-64c8-46b5-85ff-7606ce1dfd34
feature: B2B, Orders, Payments, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# MDVA-37224: impossibile pagare un &quot;preventivo negoziabile&quot; con PayFlow Pro

La patch MDVA-37224 risolve il problema quando i clienti non sono in grado di pagare per un **Offerta negoziabile** con Paypal PayFlow Pro. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23. L&#39;ID della patch è MDVA-37224. Il problema è pianificato per la risoluzione in Adobe Commerce versione 2.4.3.

## Prodotti e versioni interessati

* La patch è stata progettata per Adobe Commerce su infrastruttura cloud 2.3.6-p1
* La patch è compatibile anche con Adobe Commerce on-premise e Adobe Commerce on cloud infrastructure 2.3.3-2.4.2-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Prerequisiti</u>:

* Adobe Commerce con modulo B2B installato
* Funzionalità aziendale abilitata
* **Offerta negoziabile** funzionalità abilitata
* Esiste già un utente della società
* Il metodo di pagamento PayPal PayFlow Pro è abilitato e configurato
* Il metodo di pagamento PayPal PayFlow Pro è consentito per B2B
* Sono stati creati 2 prodotti con prezzi diversi

<u>Passaggi da riprodurre</u>:

1. Apri la vetrina.
1. Aggiungi **Prodotto 1** al carrello.
1. Creare un **Offerta negoziabile** per **Prodotto 1**.
1. Aggiungi **Prodotto 2** al carrello.
1. Da Amministratore, accetta **Offerta negoziabile** creato nel passaggio 3.
1. Dalla vetrina, apri **Offerta negoziabile** e procedi al pagamento.
1. Seleziona la **Metodo di pagamento** = *PayPal PayFlow Pro* alla **Revisione e pagamenti** passaggio.
1. Effettua l’ordine.

<u>Risultati previsti</u>:

* L’ordine è stato effettuato correttamente, come previsto.
* PayPal invia un&#39;e-mail con le informazioni corrette al cliente, come previsto.

<u>Risultati effettivi</u>:

* La pagina Web si blocca e non completa l&#39;ordine.
* PayPal invia una conferma al cliente con valori pari a zero, simile a questo esempio:

```php
Order ID: A1xxxxxxxxx
Order Placed: Monday, April 21, 2021 01:12:12 PM PDT

Shipping Amount: $0.00
Tax Amount: $0.00
Amount of Transaction: $0.00
Payment Type: Visa

BILL TO
--------
US
```


## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* 
   * [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sezione.
