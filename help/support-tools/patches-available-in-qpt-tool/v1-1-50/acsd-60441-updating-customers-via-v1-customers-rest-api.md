---
title: 'ACSD-60441: errore generato dall''aggiornamento dei clienti tramite l''endpoint API V1/customers [!DNL REST] '
description: Applica la patch ACSD-60441 per risolvere il problema di Adobe Commerce per cui l’aggiornamento dei clienti tramite V1/customers [!DNL REST] API quando si utilizza il token di accesso all’integrazione generato dal back-end genera un errore.
feature: REST, Customers
role: Admin, Developer
exl-id: fdc18060-5c6d-4f95-84d3-9ad120fe3a7d
source-git-commit: 06f751e43ef825c0eb29cb9b42eb41f07c308625
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-60441: errore generato dall&#39;aggiornamento dei clienti tramite l&#39;endpoint API [!DNL REST] di `V1/customers`

La patch ACSD-60441 risolve il problema per cui l&#39;aggiornamento dei clienti tramite l&#39;API `V1/customers` [!DNL REST] quando si utilizza il token di accesso all&#39;integrazione generato dal back-end causa un errore. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50. L’ID della patch è ACSD-60441. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p8

**Compatibile con le versioni di Adobe Commerce**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p9, 2.4.5-p8, 2.4.6-p6, 2.4.7-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Errore durante l&#39;aggiornamento dei clienti tramite l&#39;endpoint API [!DNL REST] di `V1/customers` quando si utilizza il token di accesso all&#39;integrazione generato dal backend.

<u>Passaggi da riprodurre</u>:

1. Crea un’integrazione da Admin.
1. Invia una richiesta [!DNL POST] a `rest/default/V1/customers/<customer_id>` utilizzando il token di integrazione.

   ```json
   {
     "customer": {
       "email": "roni_cost@example.com",
       "firstname": "Veronica",
       "lastname": "Costello"
     }
   }
   ```

<u>Risultati previsti</u>:

I dati del cliente vengono aggiornati.

<u>Risultati effettivi</u>:

Viene visualizzato il seguente errore:

    &quot;json
    &lbrace;
    &quot;message&quot;: &quot;Esiste già un cliente con lo stesso indirizzo e-mail in un sito Web associato.&quot;,
    &quot;trace&quot;: ...
    &rbrace;
    &quot;

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
