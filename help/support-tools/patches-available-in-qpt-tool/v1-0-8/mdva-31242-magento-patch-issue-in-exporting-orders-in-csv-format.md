---
title: "MDVA-31242: problema nell’esportazione degli ordini in formato CSV"
description: La patch MDVA-31242 risolve il problema relativo a un errore durante l'esportazione di ordini in formato CSV. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8. Il problema è stato risolto in Adobe Commerce 2.4.2.
exl-id: 1e343f23-5b10-492b-885f-8113ace4777f
feature: B2B, Data Import/Export, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# MDVA-31242: problema durante l&#39;esportazione degli ordini in formato CSV

La patch MDVA-31242 risolve il problema relativo a un errore durante l&#39;esportazione di ordini in formato CSV. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8. Il problema è stato risolto in Adobe Commerce 2.4.2.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce sull’infrastruttura cloud 2.4.0

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (metodi di distribuzione) 2.3.0 - 2.4.0-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Passaggi da riprodurre</u>:

1. Accedi al backend di amministrazione.
1. Abilita **Azienda** a **Negozi** > **Configurazione** > **Caratteristiche B2B**.
1. Vai a **Vendite** > **Ordini**.
1. Fai clic su **Colonna** > **Nome dell’azienda** casella di controllo.
1. Inserisci un valore in **Filtri** > **Nome dell’azienda** campo di testo.
1. Fai clic su **Applica filtri** pulsante.
1. Fai clic su **Esporta** > **CSV** > **Esporta** pulsante.

<u>Risultati previsti</u>:

La finestra a comparsa del file selezionato viene aperta come previsto.

<u>Risultati effettivi</u>:

Schermata bianca con l&#39;errore *Si è verificato un errore durante l&#39;elaborazione della richiesta* viene visualizzata l&#39;eccezione.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
