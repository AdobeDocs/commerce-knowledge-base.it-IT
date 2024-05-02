---
title: "MDVA-43201: errore durante l'utilizzo del campo DOB con PT delle impostazioni internazionali"
description: La patch MDVA-43201 risolve il problema relativo all'errore che si verifica quando si utilizza l'attributo DOB del cliente nel modulo di registrazione per le impostazioni locali portoghesi. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10. L'ID della patch è MDVA-43201. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
exl-id: 02979378-adc1-4a1a-93bf-a35ad50e6b80
feature: B2B, Cache
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-43201: errore durante l&#39;utilizzo di un campo DOB con PT delle impostazioni internazionali

La patch MDVA-43201 risolve il problema relativo all&#39;errore che si verifica quando si utilizza l&#39;attributo DOB del cliente nel modulo di registrazione per le impostazioni locali portoghesi. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10. L&#39;ID della patch è MDVA-43201. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando si aggiunge l&#39;attributo del cliente DOB al modulo di registrazione cliente per le impostazioni internazionali portoghesi, il modulo restituisce l&#39;errore *L&#39;argomento 1 passato a iterator_to_array() deve implementare l&#39;interfaccia travesable, null specificato*.

<u>Prerequisiti</u>:

I moduli B2B sono installati.

<u>Passaggi da riprodurre</u>:

1. Vai a Amministratore > **Negozi** > **Configurazione** > **Generale** > **Opzioni internazionali**, imposta Lingua su **Portoghese (Portogallo)** e fai clic su **Salva**.
1. Reindicizzare e cancellare la cache.
1. Vai a **Negozi** > **Attributo** > **Cliente**.
1. Apri attributo cliente DOB e imposta **Mostra in vetrina** a **Sì**.
1. Seleziona tutto da **Modulo da utilizzare in**.
1. Salva l’attributo.
1. Vai alla pagina Crea nuovo account nel front-end.

<u>Risultati previsti</u>:

Il modulo di registrazione cliente per l’archivio portoghese non fornisce alcun errore quando si aggiunge l’attributo DOB.

<u>Risultati effettivi</u>:

Il modulo di registrazione cliente per l’archivio portoghese restituisce un errore quando si aggiunge l’attributo DOB.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
