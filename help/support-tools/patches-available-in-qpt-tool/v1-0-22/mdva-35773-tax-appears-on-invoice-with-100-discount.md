---
title: "MDVA-35773: l'imposta viene visualizzata sulla fattura con uno sconto del 100%"
description: La patch di MDVA-35773 risolve il problema di non visualizzare il totale complessivo come zero nella fattura per gli ordini con uno sconto del 100%. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22. L'ID della patch è MDVA-35773. Il problema è stato risolto nella versione 2.4.3 di Adobe Commerce.
exl-id: 895cb7d3-be9f-4864-9658-87ee0471f556
feature: Invoices, Marketing Tools, Orders, Personalization, Taxes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# MDVA-35773: l&#39;imposta viene visualizzata sulla fattura con uno sconto del 100%

La patch di MDVA-35773 risolve il problema di non visualizzare il totale complessivo come zero nella fattura per gli ordini con uno sconto del 100%. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22. L&#39;ID della patch è MDVA-35773. Il problema è stato risolto nella versione 2.4.3 di Adobe Commerce.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.6

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce on-premise e Adobe Commerce sull’infrastruttura cloud 2.3.6-2.3.7 e 2.4.1-2.4.2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Passaggi da riprodurre</u>:

1. Passa a **Archivi** > **Impostazioni** > **Configurazione** > **Vendite** > **Imposta**.
1. Imposta **Prezzi catalogo** e **Applica sconto sui prezzi** a *Imposta inclusa*.
1. Passa a **Archivi** > **Regole fiscali** > **Aggiungi nuova regola fiscale**.
1. Creare una regola fiscale (ad esempio, tutti gli Stati Uniti con un&#39;aliquota del 10%) e applicarla.
1. Passa a **Marketing** > **Regole prezzo carrello** e **Aggiungi nuova regola**.
1. Crea una regola con uno sconto del **100% per tutti gli utenti**.
1. Effettua un ordine in vetrina:

   * Scegli **Spedizione gratuita**.
   * Applica **Codice coupon**.

1. Passa a **Vendite** > **Ordini** e apri l&#39;ordine.
1. Creare una fattura per l&#39;ordine e aprirla.

<u>Risultati previsti</u>:

Totale complessivo fattura = *$0,00*.

<u>Risultati effettivi</u>:

Totale complessivo fattura = *importo imposta* creato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
