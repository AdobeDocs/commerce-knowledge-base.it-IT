---
title: '"MDVA-35197: errore "Aggiungi al carrello" di GraphQL se i prodotti aggiunti sono esauriti"'
description: La patch MDVA-35197 risolve il problema relativo alla presenza di un errore durante l'aggiunta al carrello tramite GraphQL se i prodotti aggiunti in precedenza non sono più disponibili. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17.
exl-id: 189312f7-a505-4ba4-b12d-662987e69374
feature: GraphQL, Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# MDVA-35197: errore di aggiunta al carrello di GraphQL se i prodotti aggiunti sono esauriti

La patch MDVA-35197 risolve il problema relativo alla presenza di un errore durante l&#39;aggiunta al carrello tramite GraphQL se i prodotti aggiunti in precedenza non sono più disponibili. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.6

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.5 - 2.3.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Errore durante il tentativo di aggiungere un prodotto al carrello tramite GraphQL se l’altro prodotto già presente nel carrello (aggiunto anche tramite GraphQL) non è più disponibile.

<u>Passaggi da riprodurre</u>:

1. Utilizzando GraphQL, aggiungi qualsiasi prodotto al carrello.
1. Accedi al pannello di amministrazione di Commerce e imposta il prodotto come esaurito.
1. Prova ad aggiungere un altro prodotto al carrello tramite GraphQL.

<u>Risultati previsti</u>:

I prodotti in magazzino possono essere aggiunti al carrello.

<u>Risultati effettivi</u>:

Messaggio di errore GraphQL: *Alcuni prodotti sono esauriti*. Non è possibile aggiungere un nuovo prodotto &quot;in magazzino&quot;.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
