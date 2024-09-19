---
title: "ACSD-58352: le etichette degli attributi restituiti per l'archivio predefinito vengono restituite tramite [!DNL GraphQL] API"
description: Applica la patch ACSD-58352 per risolvere il problema di Adobe Commerce per cui le etichette degli attributi restituiti per l'archivio predefinito vengono restituite tramite API [!DNL GraphQL] quando nell'intestazione della richiesta è specificata una visualizzazione archivio non predefinita.
feature: GraphQL, Returns
role: Admin, Developer
source-git-commit: 6df1ec7e2cccfbadaa88b8233ca99faf40a208c5
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---


# ACSD-58352: le etichette degli attributi restituiti per l&#39;archivio predefinito vengono restituite tramite l&#39;API [!DNL GraphQL]

La patch ACSD-58352 risolve il problema per cui le etichette degli attributi restituiti per l&#39;archivio predefinito vengono restituite tramite l&#39;API [!DNL GraphQL] quando nell&#39;intestazione della richiesta è specificata una visualizzazione archivio non predefinita. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50. L’ID della patch è ACSD-58352. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le etichette degli attributi restituiti per l&#39;archivio predefinito vengono restituite tramite l&#39;API [!DNL GraphQL].

<u>Passaggi da riprodurre</u>:

1. Abilita **[!UICONTROL Return Merchandising Authorization]**.
1. Creare un *[!UICONTROL Additional Store]* e un *[!UICONTROL Store View]* nel sito Web predefinito.
1. Modificare l&#39;attributo restituito **[!UICONTROL Reason for Return]** e aggiungere etichette per tutte le visualizzazioni dello store.
1. Crea un *[!UICONTROL Order]*.
1. Crea *[!UICONTROL Return]* per l&#39;ordine. Assicurarsi che lo stato di *[!UICONTROL Return]* sia *[!UICONTROL Pending]*.
1. Invia una query del cliente [!DNL GraphQL] con il [!UICONTROL Store View] non predefinito specificato nell&#39;intestazione:

   ```
   query {
       customer {
           returns {
               items {
                   items {
                       custom_attributes {
                           label
                           value
                       }
                   }
               }
           }
       }
   }
   ```

1. Osserva la risposta.

<u>Risultati previsti</u>

Le etichette di restituzione nella risposta [!DNL GraphQL] si riferiscono a [!UICONTROL Store View] impostato nell&#39;intestazione della richiesta.

<u>Risultati effettivi</u>:

Le etichette di ritorno nella risposta [!DNL GraphQL] sono per il [!UICONTROL Store View] predefinito.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
