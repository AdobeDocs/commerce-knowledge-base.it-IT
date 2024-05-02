---
title: "ACSD-55100 [!DNL GraphQL] non restituisce prodotti oltre i 10.000 nei risultati di ricerca"
description: Applica la patch ACSD-55100 per risolvere il problema di Adobe Commerce, in cui GraphQL non restituisce prodotti oltre *10k* nei risultati della ricerca.
feature: GraphQL, Products, Search
role: Admin, Developer
exl-id: 951e5cd4-9690-43df-9e51-deab73f9eb54
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---

# ACSD-55100 [!DNL GraphQL] non restituisce prodotti oltre i 10.000 nei risultati di ricerca

La patch ACSD-55100 risolve il problema dove [!DNL GraphQL] non restituisce prodotti oltre *10k* nei risultati della ricerca. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.46. L’ID della patch è ACSD-55100. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

[!DNL GraphQL] non restituisce prodotti oltre *10k* nei risultati della ricerca.

<u>Prerequisiti</u>:

In caso di **[!DNL OpenSearch]**, accertati di utilizzare l’ultima versione disponibile.

Per risolvere il problema segnalato, viene introdotta la funzionalità Point in Time, disponibile dopo **[!DNL OpenSearch]** e richiede la versione 2.2 della `opensearch-project/opensearch-php` pacchetto.

Tuttavia, esiste un conflitto con il `magento/magento-cloud-metapackage`, che specifica una dipendenza dal `opensearch-project/opensearch-php` che deve essere inferiore alla versione 2.0.1.


Questa dipendenza impedisce l’aggiornamento di [opensearch-project/opensearch-php] alla versione più recente 2.2.

Di conseguenza, il sistema rileva il seguente errore e restituisce risultati nulli per i prodotti che superano *10.000*.

`Namespace [createPointInTime] not found in /vendor/opensearch-project/opensearch-php/src/OpenSearch/Client.php:135`

La dipendenza esistente rende difficile aggiungere direttamente una versione al `composer.json` file e aggiorna il `opensearch-project/opensearch-php` alla versione 2.2.

Per risolvere il problema, includi la seguente riga nel `composer.json` sotto il blocco require. In seguito, ridistribuisci per aggiornare il pacchetto problematico alla versione più recente.

`"opensearch-project/opensearch-php": "2.2.0 as 2.0.0",`

<u>Passaggi da riprodurre</u>:

1. Genera il catalogo con *15k* prodotti.
1. Invia il [!DNL GraphQL]:

```
    query {
    products(
    filter: {
    # category_id:{eq:""}
    }
    , pageSize: 5, currentPage: 1

    ) {
    total_count
    page_info {
    current_page
    page_size
    total_pages
     }

     aggregations {

    attribute_code
    count
    label
    options {
    label
    value

    }
    }

    items {
    uid
    sku
    is_for_clearance
    categories {
    name
    breadcrumbs {
    category_name
    category_uid
    }
    display_mode
    description
    }
    }
    }
    }
```

<u>Risultati previsti</u>:

Totale = *15k*
Dovresti essere in grado di mostrare tutti i prodotti.

<u>Risultati effettivi</u>:

Totale = *10k*
Non è possibile visualizzare altri prodotti dopo il *10k* batch.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
