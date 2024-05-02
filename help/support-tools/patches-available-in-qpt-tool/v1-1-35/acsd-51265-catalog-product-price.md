---
title: "ACSD-51265: Ottimizzare la reindicizzazione per i prodotti in bundle"
description: Applica la patch ACSD-51265 per risolvere il problema Adobe Commerce, in cui le prestazioni di reindicizzazione "catalog_product_price" sono basse quando il sistema contiene troppi prodotti in bundle.
feature: Products, Price Indexer
role: Admin
exl-id: ddf23c19-b1ed-4064-adbc-58707eb63cc9
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# ACSD-51265: Ottimizzare la reindicizzazione per i prodotti in bundle

La patch ACSD-51265 risolve il problema in cui `catalog_product_price` le prestazioni di reindicizzazione sono basse quando nel sistema sono presenti troppi prodotti in bundle. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.35. L’ID della patch è ACSD-51265. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le prestazioni di reindicizzazione del prezzo del prodotto del catalogo sono basse quando nel sistema sono presenti troppi prodotti in bundle.

<u>Passaggi da riprodurre</u>:

1. Genera un catalogo con almeno *10.000* prodotti in bundle con opzioni di prezzo dinamiche.
1. Esegui reindicizzazione prezzo prodotto.

<u>Risultati previsti</u>

La reindicizzazione del prezzo del prodotto richiede meno di 15 minuti.

<u>Risultati effettivi</u>

La reindicizzazione del prezzo del prodotto richiede più di un’ora.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
