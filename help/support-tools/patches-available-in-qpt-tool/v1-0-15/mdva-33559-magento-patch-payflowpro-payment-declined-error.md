---
title: "Patch MDVA-33559: errore pagamento PayflowPro rifiutato"
description: La patch MDVA-33559 risolve il problema che causa il rifiuto dei pagamenti PayPal PayflowPro.
exl-id: aec57ffa-07c7-404e-985d-8ec4fdb019b1
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# Patch MDVA-33559: errore pagamento PayflowPro rifiutato

La patch MDVA-33559 risolve il problema che causa il rifiuto dei pagamenti PayPal PayflowPro.

Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15. Il problema è pianificato per la risoluzione in Adobe Commerce versione 2.4.3.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:** Adobe Commerce sull’infrastruttura cloud 2.3.5-p2

**Compatibile con le versioni di Adobe Commerce:** Adobe Commerce sull’infrastruttura cloud e Adobe Commerce on-premise 2.3.0 - 2.4.2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il problema riguarda i caratteri speciali del segno e commerciale (&amp;) e del segno di uguale (=) utilizzati nei nomi.

<u>Passaggi da riprodurre</u>:

1. Aggiungi un prodotto semplice al carrello.
1. Vai al pagamento.
1. Imposta l&#39;indirizzo di spedizione. (Esempio di indirizzo di spedizione: **Nome** = ** *Di John* **  **Cognome** = ** *Apples &amp; Oranges, Inc* **  **Indirizzo** = *1234 E Senza Nome St*  **Paese** = *STATI UNITI*  **Stato/Provincia** = *Anystate*  **Città** = *Anytown*  **Zip** = *12345*  **Telefono** = *1234567890*)
1. Imposta pagamento su **PayPal PayflowPro** e tentare di completare il pagamento.

<u>Risultati previsti</u>:

La transazione genera un pagamento corretto o un messaggio di errore corretto, come previsto.

<u>Risultati effettivi</u>:

La transazione viene rifiutata e il cliente riceve un&#39;e-mail con la dicitura &quot;La transazione è stata rifiutata&quot;.

## Applicare la patch

Per applicare singole patch, utilizzare i seguenti collegamenti, a seconda del prodotto Adobe Commerce:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili nello strumento QPT, consultare [Patch disponibili nello strumento QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sezione.
