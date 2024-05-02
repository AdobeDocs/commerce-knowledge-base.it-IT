---
title: "MDVA-37592: l'ordinamento in base al prezzo non funziona per i prodotti con prezzo zero"
description: La patch di MDVA-37592 Adobe Commerce risolve il problema relativo al funzionamento non corretto dell'ordinamento in base al prezzo per i prodotti con prezzo zero assegnato a un catalogo condiviso. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.0. L'ID della patch è MDVA-37592. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
exl-id: 30ac1e87-c32d-4e79-9ed9-d1861061d760
feature: B2B, Catalog Management, Categories, Orders, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# MDVA-37592: l&#39;ordinamento in base al prezzo non funziona per i prodotti con prezzo zero

La patch di MDVA-37592 Adobe Commerce risolve il problema relativo al funzionamento non corretto dell&#39;ordinamento in base al prezzo per i prodotti con prezzo zero assegnato a un catalogo condiviso. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.0. L&#39;ID della patch è MDVA-37592. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce sulla nostra architettura cloud 2.4.0-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i tipi di distribuzione) 2.3.6-2.4.2-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;ordinamento in base al prezzo non funziona correttamente per i prodotti con il prezzo zero assegnato a un catalogo condiviso.

<u>Prerequisiti</u>:

B2B è installato.

<u>Passaggi da riprodurre</u>:

1. Abilita catalogo condiviso.
1. Crea quattro prodotti con i seguenti prezzi e assegnali a una categoria: $ 50, $ 60, $ 70 e $ 80.
1. Crea un catalogo condiviso con i prodotti di cui sopra.
1. Imposta il prezzo personalizzato su zero per il prodotto con un prezzo di $ 70.
1. Ora crea un utente aziendale e assegnalo al catalogo condiviso appena creato.
1. Accedi con l&#39;account aziendale e individua la categoria a cui sono assegnati i prodotti.
1. Prova a ordinare per prezzo.

<u>Risultati previsti</u>:

Il prodotto con prezzo zero è ordinato correttamente.

<u>Risultati effettivi</u>:

Il prodotto con prezzo zero NON è ordinato correttamente. Viene invece ordinata in base al prezzo originale.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti a seconda del tipo di distribuzione:

* Adobe Commerce on-premise: [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’architettura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Per informazioni sulle altre patch disponibili nello strumento QPT, consultare [Patch disponibili nello strumento QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sezione.
