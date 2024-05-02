---
title: "ACSD-56546: i prodotti configurabili e bundle vengono visualizzati come esauriti nella vetrina"
description: Applica la patch ACSD-56546 per risolvere il problema di Adobe Commerce, se i prodotti configurabili e bundle vengono visualizzati come esauriti nella vetrina quando *[!UICONTROL Display Out of Stock Products]* l'opzione di configurazione è disabilitata.
feature: Storefront, Products
role: Admin, Developer
exl-id: 488e2c69-442f-45e1-aa8f-71d9c0a93950
source-git-commit: 031d5cad6727bac61c88f21fa7c84e0d2a6df331
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-56546: i prodotti configurabili e bundle vengono visualizzati come esauriti sulla vetrina

La patch ACSD-56546 risolve il problema relativo alla visualizzazione dei prodotti configurabili e del bundle come esauriti nella vetrina. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48. L’ID della patch è ACSD-56546. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I prodotti configurabili e bundle vengono visualizzati come esauriti sulla vetrina quando *[!UICONTROL Display Out of Stock Products]* è disabilitata.

<u>Passaggi da riprodurre</u>:

1. Imposta il **[!UICONTROL Display Out of Stock Products]** opzione per *No*.
1. Crea un sito web, un archivio e una visualizzazione archivio.
1. Create un&#39;origine e un magazzino, quindi assegnateli al secondo sito Web.
1. Creare un *prodotto configurabile* con due prodotti secondari. Assegna entrambi i prodotti secondari a entrambe le origini e a entrambi i siti Web.
1. Aggiorna il primo prodotto secondario con *qtà=0* in entrambe le origini.
1. Aggiorna il secondo prodotto secondario e disattivalo sul secondo sito Web.
1. Effettuare una reindicizzazione completa.
1. Controlla la categoria che contiene il prodotto configurabile sul secondo sito web.

<u>Risultati previsti</u>:

I prodotti configurabili esauriti non sono visibili sulla vetrina.

<u>Risultati effettivi</u>:

I prodotti configurabili esauriti sono visibili sulla vetrina anche quando *[!UICONTROL Display Out of Stock Products]* è disabilitata.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
