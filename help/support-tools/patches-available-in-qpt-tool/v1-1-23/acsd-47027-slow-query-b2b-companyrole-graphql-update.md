---
title: "ACSD-47027: query B2B lenta [!UICONTROL CompanyRole] [!DNL GraphQL] update"
description: Applicare la patch ACSD-47027 per risolvere il problema Adobe Commerce in caso di query B2B lenta [!UICONTROL CompanyRole] [!DNL GraphQL] aggiornamento.
exl-id: 478ae16b-7722-4469-8f8a-a38820e61ae4
feature: B2B, Companies, GraphQL, Roles/Permissions
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-47027: query B2B lenta [!UICONTROL CompanyRole] [!DNL GraphQL] aggiorna

La patch ACSD-47027 risolve il problema in cui la query B2B lenta [!UICONTROL CompanyRole] [!DNL GraphQL] l&#39;aggiornamento non funziona come previsto. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.23. L’ID della patch è ACSD-47027. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1

**Compatibile con le versioni di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Query lenta B2B [!UICONTROL CompanyRole] [!DNL GraphQL] l&#39;aggiornamento non funziona come previsto.

<u>Prerequisiti</u>:

Installa il modulo B2B.

<u>Passaggi da riprodurre</u>:

1. Nell’amministrazione di Adobe Commerce, vai a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configurations]** > **[!UICONTROL B2B Features]** e imposta **[!UICONTROL Enable Company]** a _Sì_.
1. Vai al front-end e crea un’azienda.
1. Dopo aver effettuato l’accesso come utente aziendale, vai a **[!UICONTROL My Account]** > **[!UICONTROL Roles and Permissions]** e aggiungi un nuovo ruolo.
1. Abilita [!UICONTROL dev] registro query tramite `bin/magento dev:que:enab`.
1. Ora invia quanto segue [!DNL GraphQL] richiesta (id è il [!UICONTROL base64] id ruolo codificato):

   <pre><code>
   mutation {
   updateCompanyRole(
      input: {
         id: "Mg=="
         permissions: [
         "Magento_Company::view"
         "Magento_Company::view_account"
         "Magento_Company::user_management"
         "Magento_Company::roles_view"
        ]
      }
    ) {
      role {
         id

         name

         permissions {
         id

         text

         children {
            id

            text

            children {
               id

               text
             }
           }
         }
       }
     }
   }
   </code></pre>

1. Controlla il registro delle query.
1. Puoi vedere che la query precedente viene eseguita. Questa query viene eseguita in `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources`.

<u>Risultati previsti</u>:

Il `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources` deve essere ottimizzato per evitare di caricare tutti i dati disponibili nella **[!UICONTROL company_permissions]** Tabella DB.

<u>Risultati effettivi</u>:

Adobe Commerce esegue una query senza alcun filtro. In presenza di un numero elevato di record, la preparazione della raccolta dei dati da parte di Adobe Commerce richiede molto tempo.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori. 

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
