---
title: "MDVA-31282: doppia autorizzazione su Paypal PayFlow Pro"
description: La patch MDVA-31282 risolve il problema quando si verificano doppie autorizzazioni su Paypal PayFlow Pro in Adobe Commerce. Le doppie autorizzazioni hanno anche l'effetto di aggirare i filtri antifrode di PayFlow Pro e raddoppiare le tariffe delle transazioni. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7.
exl-id: f239012e-e1bd-474b-aad2-7218ec3a3d1b
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# MDVA-31282: doppia autorizzazione su Paypal PayFlow Pro

La patch MDVA-31282 risolve il problema quando si verificano doppie autorizzazioni su Paypal PayFlow Pro in Adobe Commerce. Le doppie autorizzazioni hanno anche l&#39;effetto di aggirare i filtri antifrode di PayFlow Pro e raddoppiare le tariffe delle transazioni. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce sull’infrastruttura cloud 2.3.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.2 - 2.3.3 e 2.3.5 - 2.3.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le doppie autorizzazioni si verificano in PayPal PayFlow Pro in Adobe Commerce che hanno l&#39;effetto di aggirare i filtri antifrode di PayFlow Pro e raddoppiare le tariffe delle transazioni.

<u>Prerequisiti</u>:

Configurare il metodo di pagamento PayPal PayFlow Pro.

<u>Passaggi da riprodurre</u>:

1. Vai al front-end come cliente ospite.
1. Aggiungi prodotti al **carrello** dalle pagine dei prodotti.
1. Procedi a **Estrai**.
1. Specificare **Indirizzo di spedizione** come indirizzo nel paese \#1 (ad esempio: indirizzo Regno Unito) e selezionare un metodo di spedizione.
1. Seleziona **PayPal PayFlow Pro** come metodo di pagamento. Specifica l&#39;**indirizzo di fatturazione** come indirizzo nel paese \#2 (esempio: indirizzo USA).
1. Immettere i dati della carta di credito e inserire l&#39;ordine.
1. Passa a **Vendite** > **Ordini** nell&#39;amministratore e osserva l&#39;ordine creato.

<u>Risultati previsti</u>:

* Il blocco Informazioni sul pagamento visualizza: *&quot;Filtri di frode attivati: RESPMSG: sotto revisione da Fraud Service*. *L&#39;ordine è nello stato di frode sospetta&quot;*.
* Paypal PayFlow Pro mostra una singola transazione di autorizzazione come previsto.

<u>Risultati effettivi</u>:

* Il blocco Informazioni sul pagamento visualizza: *&quot;Filtri di frode attivati: RESPMSG: sotto revisione da Fraud Service*. *Stato dell&#39;ordine in elaborazione&quot;*.
* Paypal PayFlow Pro mostra le transazioni con doppia autorizzazione.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
