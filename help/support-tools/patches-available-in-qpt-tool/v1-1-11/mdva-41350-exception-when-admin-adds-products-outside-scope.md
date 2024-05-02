---
title: "MDVA-41350: eccezione quando l’amministratore aggiunge prodotti che non rientrano nel loro accesso"
description: La patch di MDVA-41350 risolve il problema che causa un errore di eccezione anziché una notifica di accesso limitato quando un utente amministratore aggiunge un prodotto nell'ordine tramite SKU che non è accessibile. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11. L'ID della patch è MDVA-41350. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: 3a96d029-5350-4dd6-aad3-2f2cdd5e65ac
feature: Admin Workspace, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-41350: eccezione quando l&#39;amministratore aggiunge prodotti al di fuori del proprio accesso

La patch di MDVA-41350 risolve il problema che causa un errore di eccezione anziché una notifica di accesso limitato quando un utente amministratore aggiunge un prodotto nell&#39;ordine tramite SKU che non è accessibile. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11. L&#39;ID della patch è MDVA-41350. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando un utente amministratore con accesso limitato aggiunge un prodotto tramite SKU all’esterno del proprio accesso nell’ordine, si verifica un’eccezione invece di un messaggio di notifica dell’accesso limitato.

<u>Passaggi da riprodurre</u>:

1. Accedi all’amministratore come utente con accesso solo a un sito web specifico.
1. Vai a **Vendite** > **Ordini** e fai clic su **Crea nuovo ordine**.
1. Seleziona un cliente e una vista Store.
1. Fai clic su **Aggiungi prodotti per SKU**.
1. Cerca uno SKU non assegnato ad alcun sito Web o non assegnato al sito Web a cui hai accesso.
1. Clic **Aggiungi all&#39;ordine**.

<u>Risultati previsti</u>:

Viene visualizzato un messaggio di errore appropriato.

<u>Risultati effettivi</u>:

Si verifica un&#39;eccezione.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
