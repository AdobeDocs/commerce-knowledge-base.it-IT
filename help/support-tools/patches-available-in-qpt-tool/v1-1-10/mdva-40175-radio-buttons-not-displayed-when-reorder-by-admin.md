---
title: "MDVA-40175: pulsanti di scelta non visualizzati durante il riordino"
description: La patch di MDVA-40175 risolve il problema relativo alla mancata visualizzazione dei pulsanti di scelta quando gli utenti tentano di riordinare il sistema. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10. L'ID della patch è MDVA-40175. Il problema è stato risolto in Adobe Commerce 2.4.3.
exl-id: 307c450d-9f53-40b7-b2f5-d867850c043a
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# MDVA-40175: pulsanti di scelta non visualizzati durante il riordino

La patch di MDVA-40175 risolve il problema relativo alla mancata visualizzazione dei pulsanti di scelta quando gli utenti tentano di riordinare il sistema. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10. L&#39;ID della patch è MDVA-40175. Il problema è stato risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I pulsanti di scelta non vengono visualizzati nella sezione Informazioni su pagamento e spedizione quando gli utenti tentano di riordinare.

<u>Prerequisiti</u>:

1. Viene creato un account cliente con un indirizzo di spedizione e un indirizzo di fatturazione.
1. Viene creato un prodotto semplice.
1. Sono configurati diversi metodi di consegna.
1. Viene creato almeno un ordine.

<u>Passaggi da riprodurre</u>:

1. Vai al pannello di amministrazione > **Vendite** > **Ordini**.
1. Seleziona l’ordine creato.
1. Fai clic sul collegamento **Visualizza**.
1. Fare clic sul pulsante **Riordina**.
1. Scorri verso il basso la pagina fino alla sezione **Informazioni su pagamento e spedizione**.
1. Fare clic su **Fare clic per modificare il metodo di spedizione**.

<u>Risultati previsti</u>:

Viene visualizzato l’elenco dei metodi di consegna con i pulsanti di scelta.

<u>Risultati effettivi</u>:

Viene visualizzato l’elenco dei metodi di consegna senza pulsanti di scelta.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella documentazione per gli sviluppatori.
