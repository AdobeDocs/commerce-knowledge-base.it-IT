---
title: 'ACSD-45754: punti premio non aggiunti dopo l’applicazione del coupon al carrello'
description: La patch ACSD-45754 risolve il problema in cui i punti premio non vengono aggiunti dopo l’applicazione di un coupon al carrello. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18. L’ID della patch è ACSD-45754. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.
exl-id: 957713c0-3e2e-4dc9-8924-2ae84c817e47
feature: Orders, Rewards, Shopping Cart
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# ACSD-45754: punti premio non aggiunti dopo l’applicazione del coupon al carrello

La patch ACSD-45754 risolve il problema in cui i punti premio non vengono aggiunti dopo l’applicazione di un coupon al carrello. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18. L’ID della patch è ACSD-45754. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.1 - 2.4.5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I punti premio non vengono aggiunti dopo l’applicazione di un coupon al carrello.

<u>Prerequisiti</u>:

Il metodo di pagamento PayPal è configurato.

<u>Passaggi da riprodurre</u>:

1. Crea tassi di cambio punti premio andando in **Store** > **Altre impostazioni** > **Premi tassi di cambio**.
1. Crea una regola di prezzo del carrello con un codice coupon per applicare 100 punti premio ai clienti connessi.
1. Consulta un prodotto come cliente connesso con PayPal e il codice del coupon.
1. Controlla la cronologia dei punti premio nell&#39;account cliente dell&#39;amministratore.

<u>Risultati previsti</u>:

I punti premio vengono aggiunti al cliente in base alla regola del prezzo.

<u>Risultati effettivi</u>:

Al cliente non vengono aggiunti punti premio.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella documentazione per gli sviluppatori.
