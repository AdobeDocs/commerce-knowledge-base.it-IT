---
title: "MDVA-30845: il checkout interrompe la connessione al provider di spedizione"
description: La patch di MDVA-30845 risolve il problema relativo alla visualizzazione dell'errore *Non sono disponibili virgolette per l'ordine in questo momento* quando non si riesce a connettersi a UPS XML/USPS/DHL durante il check-out e non è disponibile alcun altro metodo di spedizione. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.2.
exl-id: 7be54213-1762-431b-bd3b-080c3d45f492
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# MDVA-30845: il checkout interrompe la connessione al provider di spedizione

La patch di MDVA-30845 risolve il problema che causa l&#39;errore *Nessun preventivo disponibile per l&#39;ordine in questo momento* quando non si riesce a connettersi a UPS XML/USPS/DHL durante l&#39;estrazione e non è disponibile alcun altro metodo di spedizione. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.2.

## Prodotti e versioni interessati

**La patch è stata creata per Adobe Commerce versione:** Adobe Commerce su infrastruttura cloud 2.3.5-p2.

**Compatibile con le versioni di Adobe Commerce:** Adobe Commerce on-premise e Adobe Commerce on cloud infrastructure 2.3.5-2.3.6.

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Durante l&#39;estrazione, *Non sono disponibili preventivi per questo ordine al momento* viene visualizzato l&#39;errore quando non si riesce a connettersi a UPS XML/USPS/DHL e nessun altro metodo di spedizione non è disponibile.

<u>Passaggi da riprodurre:</u>

1. Crea un prodotto.
1. Abilita e configura il metodo di spedizione XML UPS.
1. Aggiungi il prodotto al carrello sulla vetrina.
1. Verificare che siano disponibili i metodi di spedizione UPS e la spedizione a tariffa fissa.
1. Modifica il file host per impedire la connessione di USP al relativo gateway.
1. Nella vetrina, prova a ottenere le tariffe e procedi di nuovo al pagamento.

<u>Risultato effettivo:</u>

*Non sono disponibili preventivi per questo ordine in questo momento* è visualizzato un errore e la spedizione a tariffa fissa non è disponibile.

<u>Risultato previsto:</u>

Non viene visualizzato alcun messaggio di errore e la spedizione a tariffa fissa è disponibile.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.


## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
