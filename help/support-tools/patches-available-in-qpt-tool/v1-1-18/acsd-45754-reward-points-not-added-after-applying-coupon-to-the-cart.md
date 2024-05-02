---
title: "ACSD-45754: punti premio non aggiunti dopo l’applicazione del coupon al carrello"
description: La patch ACSD-45754 risolve il problema in cui i punti premio non vengono aggiunti dopo l’applicazione di un coupon al carrello. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18. L’ID della patch è ACSD-45754. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.
exl-id: 957713c0-3e2e-4dc9-8924-2ae84c817e47
feature: Orders, Rewards, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# ACSD-45754: punti premio non aggiunti dopo l’applicazione del coupon al carrello

La patch ACSD-45754 risolve il problema in cui i punti premio non vengono aggiunti dopo l’applicazione di un coupon al carrello. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18. L’ID della patch è ACSD-45754. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.1 - 2.4.5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I punti premio non vengono aggiunti dopo l’applicazione di un coupon al carrello.

<u>Prerequisiti</u>:

Il metodo di pagamento PayPal è configurato.

<u>Passaggi da riprodurre</u>:

1. Creare i tassi di cambio dei punti premio andando su **Archivia** > **Altre impostazioni** > **Tassi di cambio premio**.
1. Crea una regola di prezzo del carrello con un codice coupon per applicare 100 punti premio ai clienti connessi.
1. Consulta un prodotto come cliente connesso con PayPal e il codice del coupon.
1. Controlla la cronologia dei punti premio nell&#39;account cliente dell&#39;amministratore.

<u>Risultati previsti</u>:

I punti premio vengono aggiunti al cliente in base alla regola del prezzo.

<u>Risultati effettivi</u>:

Al cliente non vengono aggiunti punti premio.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
