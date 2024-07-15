---
title: "MDVA-36253: totale errato nel mini carrello dopo l’eliminazione dell’elemento"
description: La patch MDVA-36253 risolve il problema relativo al mancato aggiornamento del prezzo del prodotto se si torna alla pagina del mini carrello dopo aver eliminato un prodotto durante la fase di pagamento con spedizione multipla. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22. L'ID della patch è MDVA-36253. Il problema è stato risolto in Adobe Commerce 2.4.3.
exl-id: cbd436d7-7fbd-46dd-97cf-30f709da1ce5
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-36253: totale errato nel mini carrello dopo l&#39;eliminazione dell&#39;elemento

La patch MDVA-36253 risolve il problema relativo al mancato aggiornamento del prezzo del prodotto se si torna alla pagina del mini carrello dopo aver eliminato un prodotto durante la fase di pagamento con spedizione multipla. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22. L&#39;ID della patch è MDVA-36253. Il problema è stato risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.4.1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.0-2.4.1-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Totale errato nel mini carrello dopo l&#39;eliminazione dell&#39;elemento.

<u>Passaggi da riprodurre</u>:

1. Accedi come cliente con almeno un indirizzo.
1. Aggiungi quattro prodotti al carrello (prezzo = $ 10 per ciascuno).
1. Vai al carrello e fai clic su **Estrai con più indirizzi**.
1. Rimuove un elemento.
1. Torna alla home page.
1. Apri il carrello e controlla il prezzo totale.

<u>Risultati previsti</u>:

Il totale è di 30 dollari.

<u>Risultati effettivi</u>:

Il totale è di 40 dollari.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
