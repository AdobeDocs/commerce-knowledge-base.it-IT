---
title: "MDVA-43726: la regola del prezzo di catalogo non viene applicata dopo la reindicizzazione parziale"
description: La patch MDVA-43726 risolve il problema che impedisce l'applicazione della regola del prezzo di catalogo basata sulla corrispondenza degli attributi a livello di archivio dopo la reindicizzazione parziale. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12. L'ID della patch è MDVA-43726. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: 70e7e1d2-e601-4fed-9274-a1a619de29e1
feature: Catalog Management, Categories, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---

# MDVA-43726: la regola del prezzo di catalogo non viene applicata dopo la reindicizzazione parziale

La patch MDVA-43726 risolve il problema che impedisce l&#39;applicazione della regola del prezzo di catalogo basata sulla corrispondenza degli attributi a livello di archivio dopo la reindicizzazione parziale. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12. L&#39;ID della patch è MDVA-43726. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.3 - 2.4.2-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La regola del prezzo di catalogo basata sulla corrispondenza degli attributi a livello di negozio non viene applicata dopo una reindicizzazione parziale.

<u>Passaggi da riprodurre</u>:

1. Imposta la modalità di indicizzazione in modo che venga eseguita secondo pianificazione.
1. Crea due attributi di prodotto configurabili. Ad esempio: Colore (campione visivo) e Dimensione (campione di testo).
1. Crea un prodotto configurabile utilizzando entrambi gli attributi creati nel passaggio 2.
1. Dopo aver creato i prodotti, crea un’ **Sì/No** digitare l&#39;attributo e renderlo visibile nelle condizioni della regola.
1. Aggiungi questo attributo al set di attributi predefinito.
1. Crea una regola del prezzo di catalogo da applicare quando questo attributo è impostato su **Sì**.
1. Apri uno dei semplici prodotti relativi al prodotto configurabile.
1. Modifica l’ambito in cui archiviare la vista e aggiorna il valore dell’attributo in **Sì**.
1. Esegui il `CRON` e controlla il prezzo sul front-end.
1. Esegui una reindicizzazione completa. Di nuovo, controlla il prezzo sul front-end.
1. Aggiorna la categoria di prodotto configurabile.
1. Esegui il `CRON` e controlla di nuovo il prezzo sul front-end.

<u>Risultati previsti</u>:

La regola di catalogo si applica correttamente senza una reindicizzazione completa utilizzando gli indicizzatori incrementali.

<u>Risultati effettivi</u>:

La regola del catalogo non si applica senza eseguire una reindicizzazione completa.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
