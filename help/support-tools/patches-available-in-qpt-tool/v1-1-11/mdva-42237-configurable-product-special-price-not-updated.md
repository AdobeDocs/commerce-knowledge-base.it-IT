---
title: "MDVA-42237: prezzo speciale del prodotto configurabile non aggiornato"
description: La patch MDVA-42237 risolve il problema che impedisce l'aggiornamento del prezzo speciale del prodotto configurabile in seguito alle modifiche del prezzo del sottoprodotto. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11. L'ID della patch è MDVA-42237. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: 3e890448-8368-4eb2-ab64-c04cdacf20bb
feature: Admin Workspace, Configuration, Orders, Personalization, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# MDVA-42237: prezzo speciale del prodotto configurabile non aggiornato

La patch MDVA-42237 risolve il problema che impedisce l&#39;aggiornamento del prezzo speciale del prodotto configurabile in seguito alle modifiche del prezzo del sottoprodotto. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11. L&#39;ID della patch è MDVA-42237. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il prezzo speciale del prodotto configurabile non viene aggiornato in seguito alle modifiche apportate al prezzo del sottoprodotto.

<u>Passaggi da riprodurre</u>:

1. Vai a **Amministrazione** > **Sistema** > **Gestione indice** e imposta **Modalità indice** su **Aggiorna in base alla pianificazione** per tutti gli indici.
1. Crea un prodotto configurabile con un prodotto semplice e imposta un prezzo speciale per il sottoprodotto.
1. Verifica che il prezzo speciale si rifletta sullo Storefront.
1. Rimuovere il prezzo speciale utilizzando GraphQL e ricontrollare il prezzo del prodotto sul Negozio.

<u>Risultati previsti</u>:

Il prezzo speciale non viene più visualizzato sullo Store.

<u>Risultati effettivi</u>:

Il prezzo non viene aggiornato sullo Store.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella documentazione per gli sviluppatori.
