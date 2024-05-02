---
title: "MDVA-23845: impossibile visualizzare l'anteprima del modello e-mail quando è abilitata la minimizzazione JS"
description: La patch del Magento MDVA-23845 risolve il problema quando non è possibile visualizzare l'anteprima del modello e-mail in Admin quando è abilitata la minimizzazione JS.
exl-id: 08579251-a0aa-4e84-9d6a-3fa2999d9c05
feature: Communications, Marketing Tools
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# MDVA-23845: impossibile visualizzare l&#39;anteprima del modello e-mail quando è abilitata la minimizzazione JS

La patch del Magento MDVA-23845 risolve il problema quando non è possibile visualizzare l&#39;anteprima del modello e-mail in Admin quando è abilitata la minimizzazione JS.

Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20. L&#39;ID della patch è MDVA-23845. Il problema è stato risolto nella versione 2.3.5 del Magento.

## Prodotti e versioni interessati

**La patch viene creata per la versione del Magento:** Magento Commerce Cloud 2.3.3

**Compatibile con le versioni di Magento:** Magento Commerce e Commerce Cloud Magneto 2.3.2-2.3.4-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Passaggi da riprodurre</u> :

1. Abilita **Minificazione JS** in **Admin (Amministrazione) > Stores (Archivi) > Configuration (Configurazione) > JavaScript Settings (Impostazioni JavaScript) > Minify JavaScript Files (Minimizza file JavaScript)** = *Sì* .
1. Passa alla modalità di produzione del Magento.
1. Vai a **Amministratore > Marketing > Comunicazioni > Modelli e-mail** .
1. Clic **Aggiungi nuovo modello** .
1. Seleziona la **Nuovo ordine** modello.
1. Fai clic su **Carica modello** pulsante.
1. Riempi **Nome modello** con **Nuovo ordine.**
1. Fai clic su **Salva modello** pulsante.
1. Nella griglia dei modelli e-mail, fai clic su **Anteprima** collegamento in **Azioni** colonna.

<u>Risultati previsti</u> :

L’anteprima del modello e-mail viene visualizzata nella finestra a comparsa aperta, come previsto.

<u>Risultati effettivi</u> :

L’anteprima del modello e-mail non viene visualizzata nella finestra a comparsa aperta. La finestra popup è vuota e potrebbero essere visualizzati errori JS.

## Applicare la patch

Per applicare singole patch, utilizzare i seguenti collegamenti, a seconda del prodotto di Magento:

* Magento Commerce: DevDocs [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html) .
* Magento Commerce Cloud: DevDocs [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) .

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) .
* [Verifica la patch per il problema di Magento con lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) .

Per informazioni sulle altre patch disponibili nello strumento QPT, consultare [Patch disponibili nello strumento QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sezione.
