---
title: '"ACSD-49129: attributo "Content" non restituito nelle risposte API dei supporti di prodotto"'
description: Applica la patch ACSD-49129 per risolvere il problema di Adobe Commerce, in cui l’attributo *content* (*base64 image code*) non viene restituito nelle risposte API "rest/V1/products/sku/media" product media.
exl-id: b7022046-3f52-4880-81b8-977ed270773f
feature: REST, Attributes, Media, Page Content, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# ACSD-49129: attributo &quot;Content&quot; non restituito nelle risposte API per gli elementi multimediali del prodotto

La patch ACSD-49129 risolve il problema in cui *contenuto* attributo (*[!UICONTROL base64 image code]*) non viene restituito nel `rest/V1/products/sku/media` risposte API di product media. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.30. L’ID della patch è ACSD-49129. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.5-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il *contenuto* attributo (*[!UICONTROL base64 image code]*) non viene restituito nel `rest/V1/products/sku/media` risposte API di product media.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto con un’immagine.
1. Invia *API REST DI GET* richiesta a `rest/V1/products/<sku>/media` e `rest/V1/products/<sku>/media/<entryId>`.
1. Controlla le risposte API.

<u>Risultati previsti</u>

Il *contenuto* L’attributo con i dati è disponibile tramite API REST.

<u>Risultati effettivi</u>

Il *contenuto* L’attributo non è presente nelle risposte API.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
