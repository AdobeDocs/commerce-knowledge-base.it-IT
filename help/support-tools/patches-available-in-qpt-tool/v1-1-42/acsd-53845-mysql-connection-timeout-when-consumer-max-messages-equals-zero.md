---
title: 'ACSD-53845: problema di timeout della connessione MySQL quando consumer max_messages = 0'
description: Applica la patch ACSD-53845 per risolvere il problema di Adobe Commerce in cui la connessione MySQL scade quando il consumatore "max_messages = 0".
feature: REST, Configuration
role: Admin, Developer
exl-id: 68f862ed-5401-41e9-a6cc-cef44ebc1915
source-git-commit: 6fa7182a807147a00ad750966cd839ec18ffe0c7
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# ACSD-53845: problema di timeout della connessione MySQL quando il consumatore `max_messages = 0`

La patch ACSD-53845 risolve il problema relativo al timeout della connessione MySQL quando il consumatore `max_messages = 0`. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.42. L’ID della patch è ACSD-53845. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Timeout della connessione MySQL quando il consumer `max_messages = 0`.

La connessione al database verrà tuttavia ripristinata all&#39;avvio di una transazione.

<u>Passaggi da riprodurre</u>:

1. Invia una richiesta per l&#39;aggiornamento in blocco dei prodotti utilizzando l&#39;endpoint REST API `async/bulk/V1/products`.
1. Controllare lo stato nella tabella `magento_operation`.

<u>Risultati previsti</u>:

I prodotti vengono aggiornati.

<u>Risultati effettivi</u>:

1. Viene registrato un errore:

   ```
   report.CRITICAL: Message has been rejected: SQLSTATE[HY000]: General error: 2006 MySQL server has gone away [] []
   ```

1. *status* per questa operazione rimane *4* nella tabella `magento_operation`.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
