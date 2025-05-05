---
title: "ACSD-57086: gli ordini provenienti da siti web non predefiniti con termini e condizioni abilitati non vengono elaborati correttamente"
description: Applica la patch ACSD-57086 per risolvere il problema di Adobe Commerce, a causa del quale gli ordini provenienti da siti Web non predefiniti con termini e condizioni abilitati non vengono elaborati correttamente.
feature: Orders
role: Admin, Developer
source-git-commit: ab90568b0333415e73ca42b9c127a2a599f00aa7
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%

---


# ACSD-57086: gli ordini provenienti da siti Web non predefiniti con termini e condizioni abilitati vengono elaborati in modo errato

La patch ACSD-57086 risolve il problema che causa l&#39;elaborazione errata degli ordini provenienti da siti Web non predefiniti con termini e condizioni abilitati. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49. L’ID della patch è ACSD-57086. Tieni presente che questo problema è stato risolto in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Durante l&#39;utilizzo di una configurazione multi-store con elaborazione AsyncOrder, gli ordini effettuati su qualsiasi sito Web/store diverso da quello principale vengono rifiutati a causa di problemi con la gestione dell&#39;ambito nel codice consumer della coda.

<u>Passaggi da riprodurre</u>:

1. Installare [!DNL RabbitMQ] ed eseguire `bin/magento setup:upgrade` per creare le code per [!DNL RabbitMQ].
1. Configura elaborazione AsyncOrder con:

   ```bash
   bin/magento setup:config:set --checkout-async 1
   ```

1. Crea un sito Web secondario, uno store e una visualizzazione store.
1. Crea un prodotto condiviso tra entrambi i siti web.
1. Abilita termini e condizioni:
   1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]**.
   1. Imposta *[!UICONTROL Enable Terms And Conditions]* su *Sì*.
1. Configura i termini e le condizioni per entrambi i siti web:
   1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Terms And Conditions]** > **[!UICONTROL Add New Condition]**.
   1. Utilizza le seguenti impostazioni:
      * *[!UICONTROL Condition Name]*: *Qualsiasi cosa*
      * *[!UICONTROL Status]*: *[!UICONTROL Enabled]*
      * *[!UICONTROL Applied]*: *[!UICONTROL Manually]*
      * *[!UICONTROL Store View]*: *[!UICONTROL Default Store View]*
   1. Crea un’altra condizione per la seconda vista sito web/store.
1. Modificare il sito Web predefinito passando a **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**. Fare clic sul secondo sito Web, selezionare *[!UICONTROL Set as Default]* e salvare.
1. Cancella la cache con:

   ```bash
   bin/magento cache:clear
   ```

1. Vai alla vetrina e aggiungi un prodotto al carrello. Procedi al pagamento e inserisci un ordine (dovresti vedere una casella di controllo nella fase del metodo di pagamento per accettare i termini e le condizioni).
1. Dopo aver effettuato l’ordine, torna all’amministratore e cambia il sito web predefinito ripristinando il sito web principale originale e salva.
1. Cancella la cache:

   ```bash
   bin/magento cache:clear
   ```

1. Esegui il comando seguente per avviare il consumer della coda:

   ```bash
   bin/magento queue:cons:start placeOrderProcessor
   ```

<u>Risultati previsti</u>:

L&#39;ordine viene evaso e non viene automaticamente rifiutato.

<u>Risultati effettivi</u>:

Lo stato dell&#39;ordine è *rifiutato* con il seguente commento:

*L&#39;ordine non è stato effettuato. Accettare i termini e le condizioni, quindi riprovare a effettuare l&#39;ordine.*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
