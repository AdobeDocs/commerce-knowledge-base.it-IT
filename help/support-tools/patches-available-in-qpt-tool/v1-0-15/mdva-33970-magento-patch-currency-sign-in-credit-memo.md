---
title: "Patch MDVA-33970: segno di valuta nella nota di credito"
description: La patch MDVA-33970 risolve il problema relativo alla visualizzazione di un segno di dollaro ($) invece della valuta localizzata in una nota di credito. Ciò si verifica quando si utilizza un ambito **Sito Web** per un attributo **Price**.
exl-id: 47a03067-86ef-4a55-8c21-921781062b53
feature: Orders, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---

# Patch MDVA-33970: segno di valuta nella nota di credito

La patch MDVA-33970 risolve il problema relativo alla visualizzazione di un segno di dollaro ($) invece della valuta localizzata in una nota di credito. Ciò si verifica quando **Sito Web** ambito utilizzato per un **Prezzo** attributo.

Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15. Il problema è pianificato per la risoluzione in Adobe Commerce versione 2.4.3.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:** Adobe Commerce sull’infrastruttura cloud 2.3.4-p2

**Compatibile con le versioni di Adobe Commerce:** Adobe Commerce sull’infrastruttura cloud e Adobe Commerce on-premise 2.3.4 - 2.4.1-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Precondizioni</u>:

In questo esempio vengono utilizzate le seguenti impostazioni:

* Sono presenti 2 siti Web, ciascuno con un **Archivia** e un **Visualizzazione store**.
* Il **Configurazione predefinita** ha il dollaro di Singapore come **Valuta** (**Archivi > Configurazione > Generale > Impostazione valuta**):
   * **Valuta di base** = *Dollaro Singapore*
   * **Valuta di visualizzazione predefinita** = *Dollaro Singapore*
   * **Valute consentite** = *Dollaro Singapore*
* **Sito Web 1** ha un **Configurazione predefinita**.
* **Sito Web 2** ha il Ringgit malese come **Valuta**:
   * **Valuta di base** = *Ringgit malese*
   * **Valuta di visualizzazione predefinita** = *Ringgit malese*
   * **Valute consentite** = *Ringgit malese*
* Vai a **Negozi > Simboli di valuta**, e Imposta:
   * **MYR (Ringgit malese)** = *RM*
   * **SGD (Dollaro di Singapore)** = *SGD* (**Usa standard** = *Selezionato*)
* Alcuni **Prodotto** esiste.

<u>Passaggi da riprodurre</u>:

1. Crea un **Ordine** dal **Sito Web 2** Puoi impostarla come predefinita per evitare impostazioni aggiuntive.
1. Accedi a **Amministratore**.
1. Apri l’ordine appena creato.
1. Verifica che la **Simbolo valuta** = *RM*.
1. Creare un **Fattura**.
1. Verifica che la **Simbolo valuta** = *RM* nella fattura.
1. Creare un **Nota di credito**.
1. Verifica che la **Simbolo valuta**  ** ** = *RM* nel **Nota di credito**.
1. Apri **Note di credito** scheda in **Ordine**.
1. Controlla la **Simbolo valuta** nella griglia.
1. Apri **Vendite > Note di credito**.
1. Controlla la **Simbolo valuta** nella griglia.

<u>Risultati previsti</u>:

Viene utilizzato il simbolo di valuta localizzato corretto, come previsto.

<u>Risultati effettivi</u>:

Viene utilizzato il simbolo del dollaro ($), anche se non è impostato nelle impostazioni di amministrazione.

## Applicare la patch

Per applicare singole patch, utilizzare i seguenti collegamenti, a seconda del prodotto Adobe Commerce:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili nello strumento QPT, consultare [Patch disponibili nello strumento QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sezione.
