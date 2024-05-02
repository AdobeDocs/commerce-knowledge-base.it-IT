---
title: '"ACSD-51739: errore nella richiesta di "structure_id" nella richiesta GraphQL "CompanyTeam"'
description: Applica la patch ACSD-51739 per risolvere il problema Adobe Commerce in cui viene restituito un errore quando il "structure_id" viene richiesto in una richiesta GraphQL "CompanyTeam".
exl-id: 31c085e0-c8be-4709-9620-80ff360dca9a
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-51739: errore nella richiesta `structure_id` in `CompanyTeam` richiesta GraphQL

La patch ACSD-51739 risolve il problema relativo alla restituzione di un errore quando `structure_id` è richiesto in un `CompanyTeam` richiesta GraphQL. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.34. L’ID della patch è ACSD-51739. Il problema è stato risolto in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Viene restituito un errore quando `structure_id` è richiesto in un `CompanyTeam` richiesta GraphQL.

<u>Passaggi da riprodurre</u>

1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**, e impostare *[!UICONTROL Enable Company]* a *Sì*.
1. Crea un’azienda con un utente amministratore.
1. Crea un nuovo cliente (*cliente1*) e assegna la società (creata in precedenza) a questo cliente.
1. Sul front-end, accedi come utente amministratore della società.
1. Creare un team aziendale e assegnare *cliente1* al team tramite trascinamento della selezione.
1. Esegui la seguente query GraphQl aziendale, che include `CompanyTeam` con `structure_id`:

   ```GraphQL
   query{
       company {
           id
           name
           structure {
               items {
               id
               parent_id
               entity {
                   __typename
                   ... on Customer {
                       firstname
                       lastname
                       email
                       structure_id
                   }
                   ... on CompanyTeam {
                       id
                       name
                       structure_id
                   }
               }
       }
   }
   }
   }
   ```

1. Controlla la risposta di GraphQL.

<u>Risultati previsti</u>:

Non vengono restituiti errori e tutti i dati richiesti sono presenti nella risposta di GraphQL.

<u>Risultati effettivi</u>:

* La risposta contiene un *Errore interno del server*.
* `var/log/exception.log` contiene:

  ```
  report.ERROR: Cannot return null for non-nullable field "CompanyTeam.structure_id"
  ```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
