---
title: "ACSD-54324: la richiesta di richieste_elenchi di GraphQL non considera le impostazioni di paginazione"
description: Applica la patch ACSD-54324 per risolvere il problema di Adobe Commerce, in cui la richiesta di "richieste_elenchi" di GraphQL non considera le impostazioni di impaginazione e restituisce tutti i risultati.
feature: B2B, Customers, GraphQL
role: Admin, Developer
exl-id: 85297eae-bedf-4624-9758-0b68452d131b
source-git-commit: b5894687704594a4e751c230246bdf167b1b6402
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# ACSD-54324: GraphQL `requisition_lists` la richiesta non considera le impostazioni di paginazione

La patch ACSD-54324 risolve il problema in cui il GraphQL `requisition_lists` La richiesta di non considera le impostazioni di impaginazione e restituisce tutti i risultati. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.41. L’ID della patch è ACSD-54324. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

GraphQL `requisition_lists` La richiesta di non considera le impostazioni di impaginazione e restituisce tutti i risultati.

<u>Passaggi da riprodurre</u>:

1. Accedi ad admin e passa a **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.

   * Imposta *[!UICONTROL Enable Requisition List]* a *Sì*.

1. Accedi al front-end e vai a **[!UICONTROL My Requisition Lists]** dal menu principale o da **[!UICONTROL My Account]** e creare più richieste (ad esempio: 7).
1. Dopo aver generato un token cliente, esegui il codice GraphQL seguente `requisition_lists` query per il cliente.

   * Verificare che le dimensioni della pagina siano inferiori al numero totale di elenchi di richieste di acquisto creati dall&#39;utente (ad esempio: 4)

   ```
   {
   customer {
   requisition_lists(pageSize: 4, currentPage: 1) {
   items
   
   { uid name description updated_at items_count }
   total_count
   }
   }
   }
   ```

1. Il valore del `total_count` mostra 7, quando dovrebbe mostrare 4.

   Il numero di elementi indica anche 7 quando deve essere uguale al valore *dimensioni pagina*.

<u>Risultati previsti</u>:

* Numero elencato come *dimensioni pagina* viene restituito in `total_count` e non il numero totale di record.
* Il numero di elementi è uguale al *dimensioni pagina*.

<u>Risultati effettivi</u>:

Numero totale di record restituiti in `total_count`, anche se *dimensioni pagina* viene menzionato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
