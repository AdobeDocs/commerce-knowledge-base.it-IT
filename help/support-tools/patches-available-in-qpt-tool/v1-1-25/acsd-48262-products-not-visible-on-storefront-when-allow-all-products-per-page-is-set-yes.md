---
title: '"ACSD-48262: prodotti non visibili nella vetrina quando [!UICONTROL Allow All Products Per Page] è impostato [!UICONTROL Yes]'''
description: Applica la patch ACSD-48262 per risolvere il problema di Adobe Commerce, se i prodotti non sono visibili nella vetrina quando [!UICONTROL Allow All Products Per Page] è impostato su [!UICONTROL Yes].
exl-id: 327cad03-441d-4adb-8a10-802f06d3fcd1
feature: Admin Workspace, Cache, Categories, Orders, Products, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-48262: prodotti non visibili nella vetrina quando [!UICONTROL Allow All Products Per Page] è impostato *[!UICONTROL Yes]*

La patch ACSD-48262 risolve il problema se i prodotti non sono visibili nella vetrina quando [!UICONTROL Allow All Products Per Page] è impostato su *[!UICONTROL Yes]*. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25. L’ID della patch è ACSD-48262. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) >=2.4.5 &lt; 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La patch ACSD-48262 risolve il problema se i prodotti non sono visibili nella vetrina quando [!UICONTROL Allow All Products Per Page] è impostato su *[!UICONTROL Yes]*.

<u>Passaggi da riprodurre</u>:

1. Crea una categoria di test.
1. Crea un prodotto di test nella categoria di test.
1. Sfoglia la pagina del prodotto per verificare la categoria sulla vetrina e assicurati che il prodotto sia visibile.
1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** e imposta [!UICONTROL Allow All Products Per Page] impostazione su *[!UICONTROL Yes]*.
1. Cancella cache.
1. Controlla la pagina delle categorie nella vetrina.

<u>Risultati previsti</u>:

Il prodotto è visibile.

<u>Risultati effettivi</u>:

Prodotto non visibile.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.


## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
