---
title: "Patch MDVA-34192: impossibile modificare la data clienti in un determinato formato"
description: La patch MDVA-34192 risolve il problema dell’impossibilità di modificare/specificare la data di nascita del cliente nel formato gg/mm/aaaa. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.3.
exl-id: 8aa36970-b2bf-43f8-ba8f-bfc144f8d4ab
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# Patch MDVA-34192: impossibile modificare la data clienti in un determinato formato

La patch MDVA-34192 risolve il problema dell’impossibilità di modificare/specificare la data di nascita del cliente nel formato gg/mm/aaaa. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:** Adobe Commerce sull’infrastruttura cloud 2.3.5-p1

**Compatibile con le versioni di Adobe Commerce:** 2,3,4-2,3,6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La patch risolve diversi problemi. Di seguito sono riportati la descrizione e i passaggi da riprodurre per uno di essi.

Il filtro della griglia di prodotto non funziona correttamente quando si filtra utilizzando l’attributo di data personalizzato e le impostazioni locali dell’utente amministratore sono en\_GB.

<u>Passaggi da riprodurre:</u>:

1. Creare un utente amministratore il cui **Impostazioni internazionali interfaccia** è impostato su *Inglese (Regno Unito)*.
1. Crea un attributo di data con la seguente configurazione:
   * **Tipo di input del catalogo per il proprietario del negozio**: *Data*
   * **Usa nelle opzioni filtro**: *Sì*
   * **Opzioni Aggiungi a colonna**: *Sì*
1. Assegnare l&#39;attributo a una serie di attributi.
1. Vai alla pagina di modifica del prodotto, seleziona una data per il nuovo attributo utilizzando il selettore data e salva.
1. Prova a filtrare la griglia prodotti utilizzando il nuovo attributo data.

<u>Risultato previsto:</u>:

Il filtro prodotti funziona correttamente per un attributo di data personalizzato quando le impostazioni locali dell&#39;utente amministratore sono en\_GB.

<u>Risultato effettivo:</u>:

Il filtro prodotti non funziona correttamente per un attributo di data personalizzato quando le impostazioni locali dell&#39;utente amministratore sono en\_GB.

## Applicare la patch

Per applicare singole patch, utilizzare i seguenti collegamenti, a seconda del prodotto Adobe Commerce:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili nello strumento QPT, consultare [Patch disponibili nello strumento QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sezione.
