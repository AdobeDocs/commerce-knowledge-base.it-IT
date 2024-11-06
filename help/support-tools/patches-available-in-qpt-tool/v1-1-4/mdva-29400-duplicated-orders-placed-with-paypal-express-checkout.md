---
title: "MDVA-29400: ordini duplicati effettuati con PayPal Express Checkout"
description: La patch MDVA-29400 risolve il problema della creazione di ordini duplicati quando i clienti effettuano ordini con PayPal Express Checkout. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4. L'ID della patch è MDVA-29400. Il problema è stato risolto in Adobe Commerce 2.4.1.
exl-id: 75b943c8-5f7c-4d94-ae92-935428fdfcf8
feature: Checkout, Orders, Payments
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-29400: ordini duplicati effettuati con PayPal Express Checkout

La patch MDVA-29400 risolve il problema della creazione di ordini duplicati quando i clienti effettuano ordini con PayPal Express Checkout. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4. L&#39;ID della patch è MDVA-29400. Il problema è stato risolto in Adobe Commerce 2.4.1.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.3.7-p1, 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli ordini duplicati vengono creati quando gli utenti effettuano ordini con PayPal Express Checkout.

<u>Prerequisiti</u>:

Abilitazione e configurazione di PayPal Express Checkout.

<u>Passaggi da riprodurre</u>:

1. Aggiungi un prodotto al carrello.
1. Vai alla pagina Pagamento e utilizza PayPal Express come metodo di pagamento.
1. Sarà reindirizzato a paypal/express/review/page.
1. Ordinate. Verrai reindirizzato alla pagina di successo.
1. Torna a PayPal/express/review/page.
1. Fai clic sul pulsante **Inserisci ordine**.

<u>Risultati previsti</u>:

Viene creato un solo ordine.

<u>Risultati effettivi</u>:

Viene visualizzato il seguente errore: *Il token di pagamento PayPal Express non esiste*, ma il secondo ordine è stato effettuato correttamente.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
