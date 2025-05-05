---
title: 'ACSD-47027: aggiornamento B2B [!UICONTROL CompanyRole] [!DNL GraphQL]  con query lenta'
description: Applica la patch ACSD-47027 per risolvere il problema di Adobe Commerce in presenza di un aggiornamento B2B [!UICONTROL CompanyRole] [!DNL GraphQL]  lento per la query.
exl-id: 478ae16b-7722-4469-8f8a-a38820e61ae4
feature: B2B, Companies, GraphQL, Roles/Permissions
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-47027: aggiornamento B2B [!UICONTROL CompanyRole] [!DNL GraphQL] con query lenta

La patch ACSD-47027 risolve il problema che causa il mancato funzionamento previsto dell&#39;aggiornamento B2B [!UICONTROL CompanyRole] [!DNL GraphQL] della query lenta. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.23. L’ID della patch è ACSD-47027. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1

**Compatibile con le versioni di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;aggiornamento B2B [!UICONTROL CompanyRole] [!DNL GraphQL] della query lenta non funziona come previsto.

<u>Prerequisiti</u>:

Installa il modulo B2B.

<u>Passaggi da riprodurre</u>:

1. In Adobe Commerce Admin, vai a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configurations]** > **[!UICONTROL B2B Features]** e imposta **[!UICONTROL Enable Company]** su _Yes_.
1. Vai al front-end e crea un’azienda.
1. Dopo aver effettuato l&#39;accesso come utente aziendale, passare a **[!UICONTROL My Account]** > **[!UICONTROL Roles and Permissions]** e aggiungere una nuova mansione.
1. Abilita [!UICONTROL dev] registro query tramite `bin/magento dev:que:enab`.
1. Ora invia la seguente richiesta [!DNL GraphQL] (ID è l&#39;ID ruolo codificato [!UICONTROL base64]):

   <pre><code>
   mutation &lbrace;
   updateCompanyRole(
      input: &lbrace;
         id: "Mg=="
         permissions: &lbrack;
         "Magento_Company::view"
         "Magento_Company::view_account"
         "Magento_Company::user_management"
         "Magento_Company::roles_view"
        &rbrack;
      &rbrace;
    ) &lbrace;
      role &lbrace;
         id

         name

         permissions &lbrace;
         id

         text

         children &lbrace;
            id

            text

            children &lbrace;
               id

               text
             &rbrace;
           &rbrace;
         &rbrace;
       &rbrace;
     &rbrace;
   &rbrace;
   </code></pre>

1. Controlla il registro delle query.
1. Puoi vedere che la query precedente viene eseguita. Questa query viene eseguita in `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources`.

<u>Risultati previsti</u>:

È necessario ottimizzare `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources` per evitare di caricare tutti i dati disponibili nella tabella del database **[!UICONTROL company_permissions]**.

<u>Risultati effettivi</u>:

Adobe Commerce esegue una query senza alcun filtro. In presenza di un numero elevato di record, la preparazione della raccolta dei dati da parte di Adobe Commerce richiede molto tempo.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori. 

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
