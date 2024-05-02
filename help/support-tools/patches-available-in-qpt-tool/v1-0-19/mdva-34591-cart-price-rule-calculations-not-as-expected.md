---
title: "MDVA-34591: calcoli delle regole di prezzo del carrello non conformi al previsto"
description: La patch MDVA-34591 risolve il problema relativo all'applicazione della regola del prezzo del carrello con **Sconto quantità massima** non funziona correttamente se vengono applicate più regole del prezzo del carrello. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19. L'ID della patch è MDVA-34591. Il problema è pianificato per la risoluzione in Adobe Commerce versione 2.4.3.
exl-id: 1fa196bb-aab1-4364-a1b0-7c31d6d27d6d
feature: Orders, Price Rules, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 0%

---

# MDVA-34591: calcoli della regola di prezzo del carrello non conformi al previsto

La patch MDVA-34591 risolve il problema relativo alla regola del prezzo del carrello con **Sconto quantità massima applicato a** non funziona correttamente se vengono applicate più regole prezzo carrello. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19. L&#39;ID della patch è MDVA-34591. Il problema è pianificato per la risoluzione in Adobe Commerce versione 2.4.3.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.6

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce on-premise e Adobe Commerce sull’infrastruttura cloud 2.3.0-2.4.2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Passaggi da riprodurre</u>:

1. Vai all’amministratore e crea le due regole seguenti:

   * Regola 1: $10 di sconto su un massimo di tre elementi nel carrello. Imposta priorità = *3*.
   * Regola 2: 50% di sconto su tutti i prodotti del carrello. Imposta priorità = *1*.

1. Vai alla vetrina.

1. Aggiungi otto quantità di un prodotto a prezzo = *$ 51* ciascuno al carrello.

1. Controlla l’importo dello sconto nel carrello.

<u>Risultati previsti</u>:

Lo sconto calcolato corretto è di $234, come previsto.

* Calcoli:

  Regole di prezzo del carrello corrispondenti: regola 2, regola 1\
  Applica regola 2 (sconto del 50%), quindi sconto = $ 204\
  Applica regola 1 (10 articoli su 3), quindi sconto = $ 30\
  Sconto totale = MIN ( 408/2 + 10x3, 8 &#42; 51) = MIN (204 + 30, 8 &#42; 51) = $234

<u>Risultati effettivi</u>:

Lo sconto viene erroneamente calcolato a $153, causato dalla quantità errata utilizzata per calcolare il valore massimo dello sconto, in quanto l’importo fisso dello sconto viene applicato indipendentemente dall’importo dei prodotti nel carrello.

* Calcoli:

  Regole di prezzo del carrello corrispondenti: regola 2, regola 1\
  Applica regola 2 (sconto del 50%), quindi sconto = $ 204\
  Applica regola 1 (10 articoli su 3), quindi sconto = $ 30\
  Sconto totale = MIN (204 + 30, 3 &#42; 51) = $153

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sezione.
