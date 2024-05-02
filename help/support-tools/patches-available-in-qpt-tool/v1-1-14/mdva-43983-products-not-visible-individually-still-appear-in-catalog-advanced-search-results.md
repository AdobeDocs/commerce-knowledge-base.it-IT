---
title: 'MDVA-43983: i prodotti impostati come "Non visibile singolarmente" vengono visualizzati nei risultati di ricerca'
description: La patch di MDVA-43983 risolve il problema relativo alla visualizzazione dei prodotti impostati come "Non visibili singolarmente" nei risultati della ricerca avanzata del catalogo. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14. L'ID della patch è MDVA-43983. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: 2599fb6c-5b27-461b-9740-f586ae7df9f5
feature: Catalog Management, Products, Search
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# MDVA-43983: i prodotti impostati come &quot;Not Visible Individually&quot; (Non visibile singolarmente) vengono visualizzati nei risultati della ricerca

La patch di MDVA-43983 risolve il problema relativo alla visualizzazione dei prodotti impostati come &quot;Non visibili singolarmente&quot; nei risultati della ricerca avanzata del catalogo. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14. L&#39;ID della patch è MDVA-43983. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I prodotti impostati come &quot;Non visibile singolarmente&quot; vengono comunque visualizzati nei risultati della ricerca avanzata del catalogo.

<u>Passaggi da riprodurre</u>:

1. Creare un attributo con **Tipo di input del catalogo per il proprietario del negozio** as **A discesa** o **Campione visivo** (ad esempio, Colore).
1. Imposta **Uso nella ricerca** as **Sì** e **Visibile in Ricerca avanzata** as **Sì**.
1. Aggiungi alcune opzioni di attributo.
1. Creare prodotti con **Visibilità** as **Non visibile singolarmente**.
1. Assegna opzioni attributo colore.
1. Vai a **Ricerca avanzata nel catalogo** sulla vetrina.
1. Selezionare solo l&#39;opzione Attributo colore dal campo Attributo colore e lasciare vuoti i campi rimanenti o invariati.
1. Inviare un modulo di ricerca avanzata.
1. Osserva i risultati della ricerca.

<u>Risultati previsti</u>:

I prodotti impostati come &quot;Non visibile singolarmente&quot; non vengono visualizzati nei risultati della ricerca avanzata del catalogo.

<u>Risultati effettivi</u>:

I prodotti impostati come &quot;Non visibile singolarmente&quot; vengono visualizzati nei risultati della ricerca avanzata del catalogo.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
