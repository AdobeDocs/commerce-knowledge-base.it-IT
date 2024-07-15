---
title: "MDVA-37068: imposta errata visualizzata al momento dell'estrazione dei prodotti virtuali"
description: La patch MDVA-37068 risolve il problema quando nella pagina Pagine di pagamento viene visualizzata un'aliquota non corretta per i prodotti virtuali. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26. L'ID della patch è MDVA-37068. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
exl-id: ef75b41e-e79d-4947-8b74-87966642f808
feature: Cache, Checkout, Orders, Products, Taxes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# MDVA-37068: imposta errata visualizzata al momento dell&#39;estrazione dei prodotti virtuali

La patch MDVA-37068 risolve il problema quando nella pagina Pagine di pagamento viene visualizzata un&#39;aliquota non corretta per i prodotti virtuali. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26. L&#39;ID della patch è MDVA-37068. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**
Adobe Commerce sull’infrastruttura cloud 2.3.5-p2

**Compatibile con le versioni di Adobe Commerce:**
Adobe Commerce (tutti i metodi di implementazione) 2.3.1-2.4.2-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando il carrello ha solo prodotti virtuali, nella pagina Pagine di pagamento viene visualizzata un&#39;aliquota fiscale errata.

<u>Prerequisiti</u>:

1. Creare due aliquote e regole fiscali distinte per due paesi diversi, ad esempio 10% e 1%.
1. Creare un prodotto virtuale.
1. Esegui reindicizzazione e pulisci cache.

<u>Passaggi da riprodurre</u>:

1. Crea un cliente.
1. Aggiungi diversi indirizzi di fatturazione e spedizione.
1. Aggiungi un prodotto virtuale al carrello.
1. Controlla il carrello e la pagina di pagamento.

<u>Risultati previsti</u>:

L&#39;imposta visualizzata nella pagina Carrello e Pagine di pagamento è la stessa.

<u>Risultati effettivi</u>:

Le imposte visualizzate nella pagina Carrello e Pagine di pagamento NON sono uguali.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti riportati di seguito, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili nello strumento QPT, fare riferimento alla sezione [Patch disponibili nello strumento QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
