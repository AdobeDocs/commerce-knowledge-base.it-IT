---
title: "MDVA-35254: estrazione del CAPTCHA non funzionante correttamente"
description: La patch MDVA-35254 risolve il problema relativo alla mancata visualizzazione dei campi CAPTCHA dopo un numero non riuscito di tentativi di pagamento da parte di terzi. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19. L'ID della patch è MDVA-35254. Il problema è stato risolto nella versione 2.4.3 di Adobe Commerce.
exl-id: 226c672b-3740-4a87-9ea1-66892acb9fe2
feature: Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# MDVA-35254: estrazione del CAPTCHA non correttamente funzionante

La patch MDVA-35254 risolve il problema relativo alla mancata visualizzazione dei campi CAPTCHA dopo un numero non riuscito di tentativi di pagamento da parte di terzi. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19. L&#39;ID della patch è MDVA-35254. Il problema è stato risolto nella versione 2.4.3 di Adobe Commerce.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.4.1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.1-2.4.2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Passaggi da riprodurre</u>:

Configura CAPTCHA:

1. Installa e configura il provider di pagamenti di terze parti (esempio: Braintree).
1. Vai a **Store > Configurazione > Cliente > Configurazione cliente > CAPTCHA > Forms**.
1. Selezionare **Ordine di estrazione/inserimento**.
1. Mantieni **Numero di tentativi non riusciti di accedere** come predefinito (impostazione predefinita = *3*).
1. Accedi come cliente.
1. Aggiungi qualsiasi prodotto al carrello.
1. Vai alla sezione del pagamento in pagamento.
1. Seleziona **Metodo di pagamento con carta di credito** (esempio: Braintree).
1. Effettuare tre tentativi di pagamento non riusciti.

<u>Risultati previsti</u>:

Il campo CAPTCHA viene visualizzato quando viene raggiunto il numero di tentativi non riusciti.

<u>Risultati effettivi</u>:

Il campo CAPTCHA non viene mai visualizzato, solo il messaggio di errore: *Specifica il codice CAPTCHA e riprova.*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
