---
title: "Modifiche non compatibili con le versioni precedenti per  [!DNL GraphQL] `placeOrder` [!DNL API] in Adobe Commerce 2.4.6-p8"
promoted: true
description: Questo articolo fornisce una patch per il problema noto di Adobe Commerce versione 2.4.6-p8 Cloud e On-premise in cui "placeOrder" [!DNL GraphQL API] non restituisce una risposta di errore prevista, come mostrato nelle precedenti versioni della patch 2.4.6. Ciò potrebbe causare un'interruzione dell'esperienza di pagamento per i commercianti che utilizzano PWA storefront o qualsiasi altra vetrina basata su [!DNL GraphQL API] per i loro negozi.
feature: Checkout, REST, GraphQL
role: Developer
source-git-commit: 01b79c75df34de20f1ff50ab40c0a8d608ffa779
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# Modifiche non compatibili con le versioni precedenti per [!DNL GraphQL] `placeOrder` [!DNL API] in Adobe Commerce 2.4.6-p8

Questo articolo fornisce una patch per il problema noto di Adobe Commerce versione 2.4.6-p8 Cloud e On-premise in cui `placeOrder` [!DNL GraphQL API] non restituisce una risposta di errore prevista, come mostrato nelle versioni precedenti della patch 2.4.6. Ciò potrebbe causare un&#39;interruzione dell&#39;esperienza di pagamento per i commercianti che utilizzano [!DNL PWA] vetrina o qualsiasi altra vetrina basata su [!DNL GraphQL API] per i loro negozi.

>[!NOTE]
>
>In caso di problemi durante l&#39;applicazione della patch, contattare il supporto tecnico.

## Prodotti e versioni interessati

* Adobe Commerce su Cloud 2.4.6-p8
* Adobe Commerce on-premise 2.4.6-p8

## Problema

Dopo l&#39;aggiornamento alla patch di sola sicurezza di Adobe Commerce 2.4.6-p8, [`placeOrder` [!DNL GraphQL API]](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/place-order/) non restituisce una risposta di errore prevista, come nelle versioni precedenti della patch 2.4.6. Ciò potrebbe causare un&#39;interruzione dell&#39;esperienza di pagamento per i commercianti che utilizzano [!DNL PWA] vetrina o qualsiasi altra vetrina basata su [!DNL GraphQL API] per i loro negozi.

<u>Passaggio da riprodurre</u>:

Eseguire la richiesta `placeOrder` [!DNL GraphQL] in cui si prevede una risposta di errore.

<u>Risultato previsto</u>:

Ricevi una risposta di errore prevista.

<u>Risultato effettivo</u>:

Invece di una risposta di errore prevista, si riceve una risposta corretta, ma con una nuova chiave `errors` simile alla seguente:

```
{
    "data": {
        "placeOrder": {
            "order": null,
            "__typename": "PlaceOrderOutput"
        }
    }
}
```

## Soluzione per Adobe Commerce su cloud e software Adobe Commerce on-premise

Per risolvere il problema, applicare la patch.
Per scaricarlo, fai clic sul seguente collegamento:

[ac-13283-composer-patch.zip](assets/ac-13283-composer-patch.zip)

## Come applicare il cerotto

Decomprimi il file e vedi [Come applicare una patch del compositore fornita da Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) nella Knowledge Base di supporto per le istruzioni.

## Solo per gli esercenti di Adobe Commerce on Cloud: come stabilire se le patch sono state applicate

Considerando che non è possibile verificare facilmente se il problema è stato corretto, è possibile verificare se la patch è stata applicata correttamente.

<u>A tale scopo, eseguire la procedura seguente, utilizzando il file di esempio `VULN-27015-2.4.7_COMPOSER.patch` **come esempio</u>**:

1. [Installa  [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. Esegui il comando:<br>
   ![ac-13283-tell-if-patch-apply-code](assets/cve-2024-34102-tell-if-patch-applied-code.png)
1. Dovresti visualizzare un output simile a questo, dove VULN-27015 restituisce lo stato *Applicato*:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/VULN-27015-2.4.7_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```

<!-- For Step 2:
     ```bash
    vendor/bin/magento-patches -n status |grep "27015\|Status"
     ```
-->

