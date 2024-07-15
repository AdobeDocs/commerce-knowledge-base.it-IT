---
title: "Patch MDVA-34012: modifiche alla casella di controllo dell'attributo in errore"
description: La patch MDVA-34012 risolve il problema relativo alla modifica della casella di controllo di un attributo dopo un aggiornamento della pianificazione non riuscito.
exl-id: 1a8f1bea-9b6a-4984-b9f0-b2b9ceb6688f
feature: Attributes
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# Patch MDVA-34012: modifica della casella di controllo dell&#39;attributo in errore

La patch MDVA-34012 risolve il problema relativo alla modifica della casella di controllo di un attributo dopo un aggiornamento della pianificazione non riuscito.

Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.17. Il problema è pianificato per la risoluzione in Adobe Commerce versione 2.4.3.

## Prodotti e versioni interessati

**La patch è stata creata per Adobe Commerce versione:** Adobe Commerce su infrastruttura cloud 2.3.5-p2

**Compatibile con le versioni di Adobe Commerce:** Adobe Commerce su infrastruttura cloud e Adobe Commerce on-premise 2.3.1 - 2.4.2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Passaggi da riprodurre</u>:

1. Accedi ad Admin e passa a **Catalogo > Prodotti**.
1. Modificare qualsiasi prodotto semplice.
1. Cambia la visualizzazione dello store con una visualizzazione specifica dello store.
1. Salvare il prodotto con la casella di controllo **Usa valore predefinito** selezionata per un attributo (ad esempio: **Abilita attributo Prodotto**).
1. Fai clic su **Pianifica nuovo aggiornamento** per pianificare alcune modifiche (esempio: **Prezzo** o **Prezzo speciale** per una visualizzazione store specifica).
1. Attendi il completamento delle modifiche.
1. Controlli il prodotto. La casella di controllo deve essere deselezionata e deve contenere un valore di attributo store specifico.

<u>Risultati previsti</u>:

La casella di controllo dell’attributo deve rimanere la stessa e non viene modificata dopo l’aggiornamento della pianificazione, come previsto.

<u>Risultati effettivi</u>:

La casella di controllo dell&#39;attributo viene modificata dopo l&#39;aggiornamento della pianificazione.

## Applicare la patch

Per applicare singole patch, utilizzare i seguenti collegamenti, a seconda del prodotto Adobe Commerce:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili nello strumento QPT, fare riferimento alla sezione [Patch disponibili nello strumento QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
