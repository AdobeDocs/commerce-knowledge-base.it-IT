---
title: "MDVA-38852: l'inventario del catalogo blocca le tabelle riducendo le prestazioni"
description: La patch di MDVA-38852 risolve il problema relativo all'inventario del catalogo che blocca le tabelle per gli aggiornamenti, riducendo in modo significativo le prestazioni quando vengono inoltrati diversi ordini paralleli. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2. L'ID della patch è MDVA-38852. Il problema è stato risolto in Adobe Commerce 2.3.6.
exl-id: 6ecee9c8-1f39-47de-8fbc-55e30cc936af
feature: Catalog Management, Inventory, Orders
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# MDVA-38852: l&#39;inventario del catalogo blocca le tabelle riducendo le prestazioni

La patch di MDVA-38852 risolve il problema relativo all&#39;inventario del catalogo che blocca le tabelle per gli aggiornamenti, riducendo in modo significativo le prestazioni quando vengono inoltrati diversi ordini paralleli. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2. L&#39;ID della patch è MDVA-38852. Il problema è stato risolto in Adobe Commerce 2.3.6.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.3.5-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il catalogo blocca le tabelle per gli aggiornamenti che riducono notevolmente le prestazioni nei casi in cui vengono effettuati diversi ordini paralleli.

<u>Passaggi da riprodurre</u>:

1. Aggiungi un prodotto al carrello.
1. Procedi al pagamento e prova a effettuare un ordine.

<u>Risultati previsti</u>:

* Non ci sono deadlock.
* Le prestazioni non diminuiscono nei casi in cui vengono effettuati diversi ordini paralleli.

<u>Risultati effettivi</u>:

* L&#39;invio di un ordine è estremamente lento in presenza di più utenti simultanei.
* Si verificano errori di deadlock simili ai seguenti:

```SQL
"SQLSTATE[40001]: Serialization failure: 1213 Deadlock found when trying to get lock; try restarting transaction, query was:
INSERT INTO `quote_payment` (`quote_id`, `method`, `additional_information`) VALUES (?, ?, ?)"
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
