---
title: 'MDVA-26005: impossibile selezionare una categoria nella struttura per le condizioni della regola Prezzo carrello'
description: La patch MDVA-26005 risolve il problema che impediva agli utenti di selezionare una categoria nella struttura ad albero delle categorie per le condizioni della regola Prezzo carrello. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4. L'ID della patch è MDVA-26005. Il problema è stato risolto in Adobe Commerce 2.3.6.
exl-id: d3b8efc3-fd0a-4706-8851-4cecb7d3126a
feature: Categories, Orders, Price Rules, Shopping Cart
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# MDVA-26005: impossibile selezionare una categoria nella struttura per le condizioni della regola Prezzo carrello

La patch MDVA-26005 risolve il problema che impediva agli utenti di selezionare una categoria nella struttura ad albero delle categorie per le condizioni della regola Prezzo carrello. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4. L&#39;ID della patch è MDVA-26005. Il problema è stato risolto in Adobe Commerce 2.3.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.4 - 2.3.5-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Impossibile selezionare una categoria nella struttura ad albero per le condizioni della regola Prezzo carrello.

<u>Passaggi da riprodurre</u>:

1. Crea una nuova regola Prezzo carrello o modificane una esistente.
1. Andare alla sezione Azione e scegliere la categoria in Condizione.
1. Eseguire il rendering della struttura delle categorie e provare a scegliere una categoria.

<u>Risultati previsti</u>:

È possibile selezionare una categoria.

<u>Risultati effettivi</u>:

Impossibile selezionare una categoria a causa di un errore JS.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
