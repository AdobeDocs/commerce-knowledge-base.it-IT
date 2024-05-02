---
title: "MDVA-37364: l'attributo cliente personalizzato del tipo di data interrompe l'interfaccia utente della griglia"
description: La patch MDVA-37364 risolve il problema relativo all'interruzione dell'interfaccia utente di Customer Grid da parte dell'attributo cliente personalizzato del tipo di data. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2. L'ID della patch è MDVA-37364. Il problema è pianificato per la risoluzione in Adobe Commerce versione 2.4.4.
exl-id: d25baabf-45eb-403c-9f88-9c2448cc7b49
feature: Attributes, Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# MDVA-37364: l&#39;attributo cliente personalizzato del tipo di data interrompe l&#39;interfaccia utente della griglia

La patch MDVA-37364 risolve il problema relativo all&#39;interruzione dell&#39;interfaccia utente di Customer Grid da parte dell&#39;attributo cliente personalizzato del tipo di data. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2. L&#39;ID della patch è MDVA-37364. Il problema è pianificato per la risoluzione in Adobe Commerce versione 2.4.4.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0-2.4.2-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’attributo cliente personalizzato del tipo di data interrompe l’interfaccia utente della griglia clienti.

<u>Passaggi da riprodurre</u>:

1. Crea un attributo personalizzato con tipo di data:
   * Vai a **Negozi** > **Attributi** > **Aggiungi attributo**.
   * Impostare il tipo di input su Data.
   * Impostare Aggiungi a opzioni colonna su Sì.
   * Salva l’attributo.
1. Vai a **Amministratore** > **Clienti** > **Tutti i clienti**.
   * Aggiungi l’attributo personalizzato appena aggiunto alla griglia dall’opzione Colonne.
1. Crea/Modifica un cliente e imposta il valore del campo attributo data personalizzato creato.
1. Salvare, reindicizzare e cancellare la cache.
1. Vai a **Clienti** > **Tutti i clienti**.
   * Controlla la griglia clienti.

<u>Risultati previsti</u>:

La griglia clienti amministratore mostra tutti i dati, incluso il nuovo attributo personalizzato di data, senza interrompere l’interfaccia utente della griglia clienti.

<u>Risultati effettivi</u>:

L’interfaccia utente di Admin Customer Grid non funziona correttamente.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti a seconda del tipo di distribuzione:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sezione.
