---
title: "MDVA-31007: visualizzazione degli attributi di indirizzo personalizzati"
description: La patch MDVA-31007 risolve il problema relativo alla visualizzazione non corretta degli attributi degli indirizzi personalizzati nella pagina dei dettagli dell'ordine nell'area Account personale e nel backend (nella posizione **Sales &gt; Orders**). Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7. Il problema è stato risolto in Adobe Commerce 2.4.2.
exl-id: 43c82b66-395f-4e33-8312-9a1994862f5f
feature: Attributes, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---

# MDVA-31007: visualizzazione degli attributi di indirizzo personalizzati

La patch di MDVA-31007 risolve il problema relativo alla visualizzazione non corretta degli attributi degli indirizzi personalizzati nella pagina dei dettagli dell&#39;ordine nell&#39;area Account personale e nel back-end (nel percorso **Vendite > Ordini**). Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7. Il problema è stato risolto in Adobe Commerce 2.4.2.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce sull’infrastruttura cloud 2.4.0

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Passaggi da riprodurre</u>:

1. Accedi al backend di amministrazione.
1. Passa a **Archivi** > **Attributi** > **Indirizzi cliente**.
1. Creare due attributi:

   * Imposta tipo di input: *Elenco a discesa*.
   * Imposta tipo di input: *Testo*.

1. Passa a **Archivi** > **Configurazioni** > **Cliente** > **Configurazioni cliente**.
1. Seleziona *Ambito* come **Visualizzazione predefinita dello store**.
1. Espandere la sezione **Modello di indirizzo**. Aggiorna *Testo*, *Testo una riga* e *HTML* per includere i due attributi personalizzati precedenti:

   ```php
   {{depend testdropdown}}Dropdown: {{var testdropdown}}{{/depend}}    {{depend testtext}}Text: {{var testtext}}{{/depend}}
   ```

1. Apri Vetrina.
1. Crea e accedi con un utente.
1. Vai a **Il mio account** > **Rubrica** e aggiungi un nuovo indirizzo (compila i due attributi personalizzati).
1. Aggiungi un prodotto al carrello ed effettua un ordine.
1. Nella pagina di completamento dell&#39;ordine, fare clic sul collegamento **Numero ordine**.
1. Nella pagina dei dettagli dell&#39;ordine osservare la sezione **Informazioni ordine**.
1. Vai a **Backend** > **Vendite** > **Ordini**, fai clic sull&#39;ordine indicato e osserva la sezione **Informazioni indirizzo**.

<u>Risultati previsti</u>:

Sia sul front-end che sul backend, l’indirizzo di fatturazione e di spedizione viene visualizzato come previsto.

<u>Risultati effettivi</u>:

Sia nel front-end che nel back-end, l’indirizzo di fatturazione non viene visualizzato correttamente. L’opzione selezionata dell’attributo a discesa è mancante e il valore dell’attributo di input contiene il codice dell’attributo.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
