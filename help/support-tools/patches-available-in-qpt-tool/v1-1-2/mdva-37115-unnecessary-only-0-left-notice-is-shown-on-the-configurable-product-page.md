---
title: 'MDVA-37115: sulla pagina del prodotto viene visualizzato un avviso di "solo 0"'
description: La patch MDVA-37115 risolve il problema se nella pagina del prodotto configurabile viene visualizzato l'avviso non necessario *Solo 0 sinistra*. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2. L'ID della patch è MDVA-37115. Il problema è stato risolto in Adobe Commerce 2.4.3.
exl-id: 08aa6ac7-13ae-44c1-9db4-d449c3d8c985
feature: Configuration, Products, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# MDVA-37115: sulla pagina del prodotto viene visualizzato un avviso di &quot;solo 0&quot;

La patch MDVA-37115 risolve il problema che causa la visualizzazione dell&#39;avviso non necessario *Solo 0 lasciato* nella pagina del prodotto configurabile. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2. L&#39;ID della patch è MDVA-37115. Il problema è stato risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i tipi di distribuzione) 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i tipi di distribuzione) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Nella pagina del prodotto configurabile viene visualizzato un avviso non necessario di *Solo 0 lasciato*.

<u>Prerequisiti</u>:

I moduli di inventario sono installati.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto configurabile con poche opzioni.
1. Vai al front-end.
1. Apri la pagina del prodotto configurabile e seleziona un’opzione.

<u>Risultati previsti</u>:

Nessun avviso *Rimasto solo 0* visualizzato nella pagina del prodotto.

<u>Risultati effettivi</u>:

*Nella pagina del prodotto viene visualizzato solo l&#39;avviso 0 rimasto*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti a seconda del tipo di distribuzione:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento Quality Patches: è stato introdotto un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
