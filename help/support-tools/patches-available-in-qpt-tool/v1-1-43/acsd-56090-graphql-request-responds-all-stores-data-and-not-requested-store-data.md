---
title: "ACSD-56090: la risposta di GraphQL non è specifica dell’archivio"
description: Applica la patch ACSD-56090 per risolvere il problema Adobe Commerce, in cui la risposta GraphQL contiene tutti i dati di store anziché i dati specifici dell’archivio.
feature: GraphQL
role: Admin, Developer
exl-id: 129491e0-1a77-4ccc-8aba-cd0afdb26176
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-56090: la risposta di GraphQL non è specifica dell’archivio

La patch ACSD-56090 risolve il problema per cui la risposta GraphQL contiene tutti i dati di store anziché i dati specifici di store. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43. L’ID della patch è ACSD-56090. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La risposta di GraphQL contiene tutti i dati di store anziché i dati specifici dell’archivio.

<u>Passaggi da riprodurre</u>:

1. Accedi a **[!UICONTROL Admin panel]** > **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** e creare due categorie principali.
1. Ogni categoria principale deve avere una sottocategoria.
1. Accedi a **[!UICONTROL Stores]** > **[!UICONTROL All stores]** > Esistono due store con diverse categorie principali per ciascuno di essi. (Ogni Negozio deve avere almeno una visualizzazione punto vendita)
1. Vai a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > creare un prodotto con

* Tutte le principali e le sottocategorie assegnate
* Tutti i siti Web assegnati.

1. Esegui la query GraphqQL (aggiungi intestazione — store = &#39;storename ):

```
   query {
     products(filter: { url_key: { eq: "abc" } }) {
       items {
         categories {
           name
           id
           url_path
           breadcrumbs {
             category_id
             category_name
             category_level
           }
         }
       }
     }
   }
```

1. Controlla la risposta dopo l’esecuzione della query GraphqQL.

<u>Risultati previsti</u>:

Vengono restituiti dati specifici dell&#39;archivio

<u>Risultati effettivi</u>:

I dati restituiti non sono specifici dell’archivio.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
