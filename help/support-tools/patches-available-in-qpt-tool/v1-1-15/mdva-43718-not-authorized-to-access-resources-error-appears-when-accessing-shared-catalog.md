---
title: '"MDVA-43718: errore "consumer is not authorized to access resources" (Il consumatore non è autorizzato ad accedere alle risorse) durante l’accesso al catalogo condiviso"'
description: La patch MDVA-43718 risolve il problema per cui il consumer di errore *non è autorizzato ad accedere a %resources.* viene visualizzato quando si accede a un catalogo condiviso da un’integrazione personalizzata. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15. L'ID della patch è MDVA-43718. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: fa783ed4-906e-4ee6-b82a-cfe6db5ae89e
feature: Catalog Management
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-43718: errore &quot;consumer is not authorized to access resources&quot; (Il consumatore non è autorizzato ad accedere alle risorse) durante l’accesso al catalogo condiviso

La patch MDVA-43718 risolve il problema relativo all&#39;errore *il consumatore non è autorizzato ad accedere a %resources.* viene visualizzato quando si accede a un catalogo condiviso da un’integrazione personalizzata. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15. L&#39;ID della patch è MDVA-43718. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando si accede a un catalogo condiviso da un’integrazione personalizzata viene visualizzato il seguente errore: *Il consumatore non è autorizzato ad accedere a %resources*.

<u>Passaggi da riprodurre</u>:

1. Crea una nuova integrazione da Admin > **Sistema** > **Integrazione** > **Aggiungi integrazione**.
1. Aggiungi l’accesso alle seguenti risorse e attiva l’integrazione:

   * Magento_SharedCatalog::list
   * Magento_SharedCatalog::gestisci
   * Magento_Catalog::catalogo

1. Utilizzo dell’accesso all’integrazione: `rest/default/V1/sharedCatalog/1`

<u>Risultati previsti</u>:

Vengono restituiti i dettagli del catalogo condiviso.

<u>Risultati effettivi</u>:

Viene restituito il seguente errore:

```JSON
"message": "The consumer isn't authorized to access %resources.",
"resources": "Magento_SharedCatalog::sharedCatalog"
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
