---
title: "MDVA-43091: impossibile ordinare il prodotto in bundle dall'amministratore"
description: La patch MDVA-43091 risolve il problema che impediva agli utenti di ordinare il prodotto in bundle dall'amministratore Commerce. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10. L'ID della patch è MDVA-43091. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
exl-id: 77dff356-4f75-4b06-b62b-5379a4eec273
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# MDVA-43091: impossibile ordinare il prodotto in bundle dall&#39;amministratore

La patch MDVA-43091 risolve il problema che impediva agli utenti di ordinare il prodotto in bundle dall&#39;amministratore Commerce. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10. L&#39;ID della patch è MDVA-43091. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando si tenta di ordinare il prodotto in bundle dall&#39;amministratore, viene generato il seguente errore: *Impossibile utilizzare la quantità decimale per questo prodotto.*

<u>Passaggi da riprodurre</u>:

1. Installa un Adobe Commerce pulito.
1. Crea due prodotti semplici.
1. Crea un prodotto in bundle con due opzioni.
1. Crea un account cliente sul front-end.
1. Vai a **Amministratore** > **Vendite** > **Ordini** > **Crea nuovo ordine**.
   * Seleziona l’account cliente appena creato.
   * Prova ad aggiungere il prodotto nel carrello.

<u>Risultati previsti</u>:

L’utente amministratore può aggiungere al carrello il prodotto con una quantità.

<u>Risultati effettivi</u>:

L&#39;utente amministratore riceve il seguente errore: *Impossibile utilizzare la quantità decimale per questo prodotto.*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella documentazione per gli sviluppatori.
