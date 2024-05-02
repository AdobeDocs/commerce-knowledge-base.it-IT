---
title: '"MDVA-43859: errore "Nessuna entità di questo tipo con customerId =" registrato quando il cliente eliminato effettua l’accesso"'
description: La patch di MDVA-43859 risolve il problema relativo all'errore *Nessuna entità con customerId =* viene registrata quando un cliente eliminato tenta di accedere. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14. L'ID della patch è MDVA-43859. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: 62c4b6ee-88a0-40b8-9eb2-37b6cefa0b83
feature: Variables
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# MDVA-43859: errore &quot;Nessuna entità di questo tipo con customerId =&quot; registrato al momento dell&#39;accesso del cliente eliminato

La patch di MDVA-43859 risolve il problema relativo all&#39;errore *Nessuna entità di questo tipo con customerId =* viene registrato quando un cliente eliminato tenta di accedere. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14. L&#39;ID della patch è MDVA-43859. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’errore *Nessuna entità di questo tipo con customerId =* viene registrato quando un cliente eliminato tenta di accedere.

<u>Passaggi da riprodurre</u>:

1. Crea un account cliente dal front-end.
1. Esci e accedi all&#39;account cliente creato nel passaggio 1.
1. Carica il backend in un altro browser e passa alla griglia del cliente.
1. Elimina il cliente creato nel passaggio 1.
1. Torna al primo browser e prova a disconnetterti.

<u>Risultati previsti</u>:

Il cliente viene reindirizzato alla pagina di accesso senza alcun errore.

<u>Risultati effettivi</u>:

Il cliente riceve il seguente errore: *Nessuna entità di questo tipo con customerId =*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
