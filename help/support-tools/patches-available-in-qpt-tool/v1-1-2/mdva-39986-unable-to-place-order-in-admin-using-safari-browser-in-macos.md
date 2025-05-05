---
title: "MDVA-39986: impossibile effettuare ordini in amministratore nel browser Safari su macOS"
description: La patch MDVA-39986 risolve il problema che impediva agli utenti di effettuare ordini nell'amministratore utilizzando il browser Safari su macOS. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.2. L'ID della patch è MDVA-39986. Il problema è stato risolto in Adobe Commerce 2.4.3.
exl-id: a35b6253-e03f-4bdb-a3a3-fceb70588c6e
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# MDVA-39986: impossibile effettuare ordini in amministratore nel browser Safari su macOS

La patch MDVA-39986 risolve il problema che impediva agli utenti di effettuare ordini nell&#39;amministratore utilizzando il browser Safari su macOS. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.2. L&#39;ID della patch è MDVA-39986. Il problema è stato risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1 - 2.4.2-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli utenti non possono effettuare ordini presso l’amministratore utilizzando il browser Safari su macOS.

<u>Passaggi da riprodurre</u>:

1. Effettua un ordine.
1. Vai all’amministratore tramite il browser Safari su macOS e apri l’ordine creato in precedenza.
1. Fai clic su **Riordina**.
1. Prova ad aggiornare **la quantità di prodotto**.

<u>Risultati previsti</u>:

Gli utenti devono essere in grado di riordinare il file utilizzando il browser Safari su macOS.

<u>Risultati effettivi</u>:

Gli utenti ricevono un errore JS in cui viene visualizzata la rotellina che viene eseguita all’infinito.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella documentazione per gli sviluppatori.
