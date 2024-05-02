---
title: "MDVA-38559: errore restituito da /V1/customers/search API"
description: La patch MDVA-38559 risolve il problema per cui l’API `/V1/customers/search` restituisce un errore per i clienti che hanno più di un abbonamento. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15. L'ID della patch è MDVA-38559. Tieni presente che il problema è risolto in Adobe Commerce 2.4.3.
exl-id: 434fe78c-c384-4fa8-b26a-cb00007e490e
feature: REST, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# MDVA-38559: errore restituito da /V1/customers/search API

La patch MDVA-38559 risolve il problema in cui `/V1/customers/search` L’API restituisce un errore per i clienti che hanno più di una sottoscrizione. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15. L&#39;ID della patch è MDVA-38559. Tieni presente che il problema è risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

`/V1/customers/search` L’API restituisce un errore per i clienti con più di una sottoscrizione.

<u>Prerequisiti</u>:

Lo store di Adobe Commerce utilizza più di un sito web.

<u>Passaggi da riprodurre</u>:

1. Vai a **Archivia** > **Configurazione** > **Cliente** > **Configurazione cliente** > **Opzioni di condivisione account** e seleziona **Globale**.
1. Vai a **Clienti** > **Tutti i clienti**, seleziona **Modifica** su qualsiasi cliente, quindi seleziona **Newsletter**.
1. Iscriviti a una newsletter per più siti Web e salva il cliente.
1. Invia la seguente richiesta:

```REST API
V1/customers/search?searchCriteria[filterGroups][0][filters][0][field]=email&searchCriteria[filterGroups][0][filters][0][value]=test@example.com&searchCriteria[filterGroups][0][filters][0][conditionType]=eq
```

<u>Risultati previsti</u>:

Vengono visualizzati i risultati della ricerca del cliente.

<u>Risultati effettivi</u>:

Il seguente errore viene registrato in exception.log: *Esiste già un elemento (Magento\Customer\Model\Customer\Interceptor) con lo stesso ID &quot;1&quot;.*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
