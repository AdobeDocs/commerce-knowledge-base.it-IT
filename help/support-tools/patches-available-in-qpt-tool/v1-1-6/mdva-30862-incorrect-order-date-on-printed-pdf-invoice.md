---
title: 'MDVA-30862: data ordine errata nella fattura PDF stampata'
description: La patch MDVA-30862 risolve il problema relativo alla stampa di una data di ordine errata nella fattura PDF. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.6. L'ID della patch è MDVA-30862. Il problema è stato risolto in Adobe Commerce 2.4.0.
exl-id: 695f530e-6abf-4883-972d-5d9c379493a2
feature: Invoices, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# MDVA-30862: data ordine errata nella fattura PDF stampata

La patch MDVA-30862 risolve il problema relativo alla stampa di una data di ordine errata nella fattura PDF. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.6. L&#39;ID della patch è MDVA-30862. Il problema è stato risolto in Adobe Commerce 2.4.0.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.4

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.4 - 2.3.7-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La data dell&#39;ordine errata viene stampata sulla fattura PDF.

<u>Passaggi da riprodurre</u>:

1. Vai a **Vendite** > **Ordini**.
1. Selezionare un ordine e stampare la fattura.

<u>Risultati previsti</u>:

La data corrisponde alla data di acquisto.

<u>Risultati effettivi</u>:

La data (compreso il mese/anno) non corrisponde alla data di acquisto.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella documentazione per gli sviluppatori.
