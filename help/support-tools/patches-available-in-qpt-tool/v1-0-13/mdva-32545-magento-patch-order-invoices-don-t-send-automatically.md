---
title: "Patch MDVA-32545: le fatture dell'ordine non vengono inviate automaticamente"
description: La patch di MDVA-32545 risolve il problema che impedisce l'invio automatico delle e-mail di fattura al cliente per gli ordini inoltrati dall'amministratore. Questo influisce su qualsiasi metodo di pagamento con il tipo di transazione **Vendita**, come **Braintree ** o **PayPal Payflow Pro**.
exl-id: 682eaeb1-5475-4d37-9536-0605f5b9f163
feature: Invoices, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# Patch MDVA-32545: le fatture ordine non vengono inviate automaticamente

La patch di MDVA-32545 risolve il problema che impedisce l&#39;invio automatico delle e-mail di fattura al cliente per gli ordini inoltrati dall&#39;amministratore. Questo influisce su qualsiasi metodo di pagamento con tipo di transazione **Vendita**, come **Braintree** o **PayPal Payflow Pro**.

Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13. Il problema è stato risolto nella versione 2.4.2 di Adobe Commerce.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.2-p2

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud e Adobe Commerce on-premise 2.3.0 - 2.4.1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Passaggi da riprodurre</u>:

1. Abilita qualsiasi metodo di pagamento con il tipo di transazione **Vendita**. (ad esempio: **Braintree** o **PayPal Payflow Pro**.)
1. Crea un prodotto semplice.
1. Crea un account cliente nel front-end.
1. Effettua un ordine dall’Amministratore.

<u>Risultati previsti</u>:

L&#39;e-mail della fattura viene inviata automaticamente al cliente, come previsto.

<u>Risultati effettivi</u>:

L&#39;e-mail della fattura non viene inviata automaticamente al cliente.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta le [patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
