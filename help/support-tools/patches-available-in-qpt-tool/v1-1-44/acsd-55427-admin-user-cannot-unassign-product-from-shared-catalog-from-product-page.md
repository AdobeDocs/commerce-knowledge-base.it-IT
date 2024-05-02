---
title: "ACSD-55427: un amministratore non può annullare l’assegnazione di un prodotto a un **[!UICONTROL Product in Shared Catalogs]** sulla pagina del prodotto"
description: Applicare la patch ACSD-55427 per risolvere il problema di Adobe Commerce che impedisce l'annullamento dell'assegnazione di un prodotto **[!UICONTROL Product in Shared Catalogs]**.
feature: Products, B2B
role: Admin, Developer
exl-id: 1e08def1-07f6-42e0-b600-9f0bfdd6477a
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-55427: un amministratore non può annullare l’assegnazione di un prodotto da **[!UICONTROL Product in Shared Catalogs]** sulla pagina del prodotto

La patch ACSD-55427 risolve il problema che impediva di annullare l’assegnazione di un prodotto **[!UICONTROL Product in Shared Catalogs]** nella pagina del prodotto nel catalogo di Commerce Admin. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44. L’ID della patch è ACSD-55427. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Non puoi annullare l’assegnazione di un prodotto da **[!UICONTROL Product in Shared Catalogs]** nella pagina del prodotto nel catalogo di Commerce Admin.

<u>Passaggi da riprodurre</u>:

Prerequisiti: Adobe Commerce installato con B2B e **[!UICONTROL Shared Catalogs]** abilitato.
1. Crea un prodotto.
1. Passa alla dashboard del catalogo condiviso e apri il catalogo condiviso predefinito.
1. Assegnazione del prodotto al catalogo predefinito e impostazione di un prezzo inferiore al prezzo del prodotto.
1. Salva il catalogo condiviso.
1. Esegui il [!UICONTROL CRON] per aggiornare i consumer/indicizzatori.
1. Apri il prodotto e rimuovilo da sotto **[!UICONTROL Product in Shared Catalogs]** sezione.

<u>Risultati previsti</u>:

Il prodotto deve essere rimosso da in **[!UICONTROL Product in Shared Catalogs]** sezione.

<u>Risultati effettivi</u>:

Il prodotto viene ancora visualizzato in **[!UICONTROL Product in Shared Catalogs]** sezione.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
