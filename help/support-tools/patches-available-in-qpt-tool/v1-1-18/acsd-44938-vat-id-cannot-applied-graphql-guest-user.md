---
title: "ACSD-44938: VAT_ID non può essere applicato nella richiesta GraphQL per l’utente ospite"
description: La patch ACSD-44938 risolve il problema che impediva l'applicazione del VAT_ID in una richiesta GraphQL per un utente guest. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18. L’ID della patch è ACSD-44938. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.
exl-id: 18b3dfa5-b666-491e-a067-526a53294f39
feature: Admin Workspace, GraphQL
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-44938: VAT_ID non può essere applicato nella richiesta GraphQL per l’utente ospite

La patch ACSD-44938 risolve il problema che impediva l&#39;applicazione del VAT_ID in una richiesta GraphQL per un utente guest. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18. L’ID della patch è ACSD-44938. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

VAT_ID non può essere applicato in una richiesta GraphQL per un utente ospite.

<u>Passaggi da riprodurre</u>:

1. Segui i passaggi indicati nell&#39;[esercitazione su GraphQL](https://devdocs.magento.com/guides/v2.4/graphql/tutorials/checkout/checkout-shopping-cart.html) nella documentazione per sviluppatori per creare un carrello guest.
1. Provare ad applicare VAT_ID per l&#39;utente ospite che utilizza GraphQL.

<u>Risultati previsti</u>:

VAT_ID può essere applicato nello stesso modo di un cliente registrato. Consulta l&#39;articolo [createCustomerAddress mutation](https://devdocs.magento.com/guides/v2.4/graphql/mutations/create-customer-address.html) nella documentazione per gli sviluppatori.

<u>Risultati effettivi</u>:

VAT_ID non può essere applicato a un utente guest che utilizza GraphQL.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
