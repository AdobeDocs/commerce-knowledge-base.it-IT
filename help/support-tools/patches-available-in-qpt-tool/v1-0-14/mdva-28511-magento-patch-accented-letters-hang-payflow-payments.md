---
title: "MDVA-28511: le lettere accentate bloccano i pagamenti Payflow"
description: La patch MDVA-28511 risolve il problema quando i pagamenti tramite **Payflow Pro** non vengono completati per i nomi dei clienti con lettere accentate.
exl-id: ecc827e3-2a1c-4f32-a0e2-9c5792483e7d
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# MDVA-28511: le lettere accentate bloccano i pagamenti Payflow

La patch MDVA-28511 risolve il problema quando i pagamenti tramite **Payflow Pro** non vengono completati per i nomi dei clienti con lettere accentate.

Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.14. Il problema è stato risolto nella versione 2.3.6 di Adobe Commerce.

## Prodotti e versioni interessati

**La patch è stata creata per Adobe Commerce versione:** Adobe Commerce su infrastruttura cloud 2.3.5-p1

**Compatibile con le versioni di Adobe Commerce:** Adobe Commerce su infrastruttura cloud e Adobe Commerce on-premise 2.3.5 - 2.3.5-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Prerequisito</u>:

Abilita il metodo di pagamento con carta di credito **Payflow Pro**.

<u>Passaggi da riprodurre</u>:

1. Aggiungi un prodotto al carrello e continua fino alla pagina di pagamento.
1. Impostare un nome cliente con lettere accentate. (Esempio: **Ãtienne Ãillin**)
1. Procedi alle fasi di pagamento.
1. Seleziona **Payflow Pro** come **Carta di credito** e compila i dettagli della carta di credito.
1. Fai clic sul pulsante **Inserisci ordine**.

<u>Risultati previsti</u>:

L’ordine viene completato senza alcun problema, come previsto.

<u>Risultati effettivi</u>:

L’ordine non viene completato e i registri mostreranno un errore simile a questo esempio:

```php
[2020-06-12 07:50:23] report.CRITICAL: String to be escaped was not valid UTF-8 or could not be converted: �?tienne �?illini [] []
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
