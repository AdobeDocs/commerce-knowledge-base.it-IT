---
title: "MDVA-42645: l'amministratore non può rimborsare i punti premio per il credito dell'archivio disabilitato"
description: La patch MDVA-42645 risolve il problema per cui l'amministratore non può rimborsare i punti premio se la funzionalità di credito all'archivio è disabilitata. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12. L'ID della patch è MDVA-42645. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: 8e8f8c07-c1a2-4031-a2fb-cb737165dc2c
feature: Admin Workspace, Orders, Rewards, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# MDVA-42645: l&#39;amministratore non può rimborsare i punti premio per il credito dell&#39;archivio disabilitato

La patch MDVA-42645 risolve il problema per cui l&#39;amministratore non può rimborsare i punti premio se la funzionalità di credito all&#39;archivio è disabilitata. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12. L&#39;ID della patch è MDVA-42645. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;amministratore non può rimborsare i punti premio se la funzionalità di credito dell&#39;archivio è disabilitata.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto semplice.
1. Crea un nuovo account cliente e aggiungi alcuni punti premio.
1. Disattiva la funzionalità di credito per lo store accedendo a **Archivia** > Impostazioni > **Configurazione** > **Cliente** > **Configurazione cliente** > **Opzioni di credito store**.
1. Accedi come cliente a cui sono assegnati i punti premio.
1. Aggiungi un prodotto al carrello e passa a pagamento.
1. Utilizza i punti premio nella sezione pagamento e inserisci l’ordine.
1. Aprire l&#39;ordine nell&#39;amministratore e fatturarlo.
1. Fai clic sul pulsante **Nota di credito** per creare una nuova nota di credito.
1. Selezionare l&#39;opzione Rimborso punti premio nella parte inferiore e fare clic sul pulsante **Rimborso offline**.

<u>Risultati previsti</u>:

* Creazione della nota di credito completata.
* I punti premio vengono rimborsati correttamente.

<u>Risultati effettivi</u>:

Viene visualizzato il seguente messaggio di errore: *Non è possibile utilizzare un credito del punto vendita superiore all&#39;importo dell&#39;ordine.*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
