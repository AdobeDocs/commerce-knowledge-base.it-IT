---
title: "MDVA-31006: errore 10415 ordini duplicati di Paypal"
description: La patch di MDVA-31006 risolve il problema che l'utilizzo del pagamento PayPal Express per il pagamento di checkout crea ordini duplicati con un errore di 10415. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6. Il problema è stato risolto in Adobe Commerce 2.4.2.
exl-id: ff471fd3-f580-4149-83bc-67f6fce8e28d
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---

# MDVA-31006: errore 10415 ordini duplicati di Paypal

La patch di MDVA-31006 risolve il problema che l&#39;utilizzo del pagamento PayPal Express per il pagamento di checkout crea ordini duplicati con un errore di 10415. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6. Il problema è stato risolto in Adobe Commerce 2.4.2.

## Prodotti e versioni interessati

* Adobe Commerce (tutti i metodi di implementazione) 2.3.2 - 2.4.0

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’utente non viene inviato alla pagina di completamento dell’ordine di Adobe Commerce, pertanto aggiorna la pagina vuota e inserisce il secondo ordine, creando ordini duplicati.

<u>Prerequisiti</u>:

* Adobe Commerce è installato.
* Il pagamento PayPal Express Checkout è configurato.
* Accedi all’amministratore di Commerce. Vai a **Negozi** > **Configurazione** > **Vendite** > **Metodi di pagamento** > seleziona **Pagamento Paypal Express** > **Configura** > **Impostazioni avanzate** > **Ignora passaggio di revisione ordine** > *No*.

<u>Passaggi da riprodurre</u>:

1. Accedi come utente.
1. Seleziona un elemento e fai clic su **Aggiungi al carrello**.
1. Fai clic sul carrello e fai clic su **Procedi all&#39;estrazione**.
1. Procedi alla finestra PayPal Express ed effettua un pagamento.
1. Viene visualizzata la pagina Adobe Commerce Order Review (Revisione ordine).
1. Premere il tasto **Inserisci ordine** pulsante.
1. Emulazione di errore di sistema a causa di problemi di infrastruttura del server. L’utente visualizzerà una pagina vuota.
1. Aggiorna la pagina.

<u>Risultati previsti</u>:

* Il cliente viene reindirizzato alla pagina di revisione dell’ordine e visualizza un messaggio di errore &quot;*Una transazione di pagamento riuscita è già stata completata. Verifica se l&#39;ordine è stato effettuato.*&quot;
* Nel paylog, che si trova in `/var/log/payment.log`, si è verificato un 10415 di errore, ma è stato creato un solo ordine.

<u>Risultati effettivi</u>:

* Poiché il cliente non viene inviato alla pagina di successo dell’ordine di Adobe Commerce, aggiorna la pagina vuota e viene effettuato un secondo ordine, in modo da creare due ordini duplicati.
* Nel paylog, che si trova in `/var/log/payment.log`, si è verificato un 10415 di errore.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
