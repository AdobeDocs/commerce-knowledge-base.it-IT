---
title: "ACSD-49013: conferma e-mail non tradotta nelle impostazioni locali del sito web"
description: Applica la patch ACSD-49013 per risolvere il problema di Adobe Commerce per cui la conferma e-mail non viene tradotta nelle impostazioni locali del sito web durante la creazione di clienti utilizzando l’API in blocco.
exl-id: 68203bd4-021a-4736-a793-4b6663a9c66b
feature: Admin Workspace, Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# ACSD-49013: conferma e-mail non tradotta nelle impostazioni locali del sito web

La patch ACSD-49013 risolve il problema per cui la conferma e-mail non viene tradotta nelle impostazioni locali del sito web quando si creano clienti utilizzando l’API in blocco. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27. L’ID della patch è ACSD-49013. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La conferma e-mail non viene tradotta nella lingua del sito web quando si creano clienti utilizzando l’API in blocco.

<u>Passaggi da riprodurre</u>:

1. Installare una lingua diversa, ad esempio `de_DE`.
1. Configura *RabbitMQ*.
1. Eseguire `bin/magento setup:upgrade` per installare le code in RabbitMQ e configurare il Language Pack.
1. Crea un altro sito Web in [!UICONTROL Admin] > **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**.
1. Impostare le impostazioni locali del nuovo sito Web su `de_DE` in [!UICONTROL Admin] > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Locale Options]**.
1. Esegui una chiamata API per creare un account cliente utilizzando l’API in blocco. Utilizza il `website_id` corrispondente.

   `Endpoint: /rest/async/bulk/V1/customers`

   ```
   [{
       "customer": {
       "email": "test@example.com",
       "firstname": "test",
       "lastname": "test",
       "website_id": 2
       },
       "password": "Passw0rd!"
   }]
   ```

1. Eseguire `bin/magento queue:consumers:start async.operations.all --single-thread --max-messages=10`.
1. Puoi vedere che l’account del cliente è stato creato correttamente sul sito web specificato.
1. Controlla l’e-mail ricevuta per la registrazione del cliente.

<u>Risultati previsti</u>:

Poiché il cliente viene creato su un sito Web specifico, l&#39;e-mail di registrazione viene inviata utilizzando le impostazioni internazionali di tale sito Web.

<u>Risultati effettivi</u>:

Il cliente viene creato correttamente sul sito web specificato, ma l’e-mail di registrazione viene inviata utilizzando la lingua predefinita quando viene utilizzata l’API in blocco.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
