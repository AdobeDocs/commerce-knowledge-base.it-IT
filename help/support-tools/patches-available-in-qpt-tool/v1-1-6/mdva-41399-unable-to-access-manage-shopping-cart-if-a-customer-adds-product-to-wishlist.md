---
title: "MDVA-41399: impossibile accedere a Gestisci carrello se un cliente aggiunge un prodotto alla lista dei desideri"
description: La patch MDVA-41399 risolve il problema che impedisce agli utenti amministratori di accedere alla pagina Gestisci carrello se un cliente aggiunge un prodotto alla lista dei desideri. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6. L'ID della patch è MDVA-41399. Il problema è stato risolto in Adobe Commerce 2.4.2.
exl-id: 227653c6-2d20-4475-b973-b9fa58db815b
feature: Orders, Products, Shopping Cart
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# MDVA-41399: impossibile accedere a Gestisci carrello se un cliente aggiunge un prodotto alla lista dei desideri

La patch MDVA-41399 risolve il problema che impedisce agli utenti amministratori di accedere alla pagina Gestisci carrello se un cliente aggiunge un prodotto alla lista dei desideri. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6. L&#39;ID della patch è MDVA-41399. Il problema è stato risolto in Adobe Commerce 2.4.2.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.3 - 2.4.1-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli utenti amministratori non possono accedere alla pagina Gestisci carrello se un cliente aggiunge un prodotto alla lista dei desideri.

<u>Prerequisiti</u>:

1. Crea due o più prodotti.
1. Crea un cliente.
1. Abilita la modalità Sviluppatore.

<u>Passaggi da riprodurre</u>:

1. Vai a Storefront e accedi come cliente dalle precondizioni.
1. Aggiungi un prodotto alla lista dei desideri.
1. Vai al pannello di amministrazione e passa alla pagina di modifica del cliente creata, quindi fai clic sul pulsante **Gestisci carrello**.

<u>Risultati previsti</u>:

L’utente amministratore è in grado di gestire il carrello.

<u>Risultati effettivi</u>:

L&#39;utente amministratore riceve un messaggio di errore: *Si è verificato un errore. Per ulteriori dettagli, vedere il registro errori.*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
