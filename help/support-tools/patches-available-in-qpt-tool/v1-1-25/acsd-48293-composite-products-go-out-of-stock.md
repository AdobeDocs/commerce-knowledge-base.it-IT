---
title: "ACSD-48293: prodotti compositi esauriti quando i prodotti per bambini sono esauriti dopo il ripopolamento"
description: Applicare la patch ACSD-48293 per risolvere il problema Adobe Commerce relativo all'esaurimento delle scorte dei prodotti compositi quando i prodotti secondari esauriti vengono restituiti alle scorte.
exl-id: 74ca34fe-e015-4daf-a608-4756c8ab3558
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-48293: prodotti compositi esauriti quando sono esauriti i prodotti per bambini riassortiti

La patch ACSD-48293 risolve il problema relativo all&#39;esaurimento delle scorte dei prodotti compositi quando i prodotti secondari esauriti vengono restituiti alle scorte. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25. L’ID della patch è ACSD-48293. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I prodotti compositi esauriscono quando i prodotti secondari esauriti vengono restituiti alle scorte.

<u>Passaggi da riprodurre</u>:

1. Crea una visualizzazione secondaria per sito Web, store e store.
1. Crea due origini e due scorte e assegnale a ciascun sito Web.
1. Abilita l’opzione Mostra prodotti esauriti in **[!UICONTROL Store]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** > **[!UICONTROL Display Out-of-Stock Products]** = *[!UICONTROL Yes]*.
1. Creare un prodotto configurabile con un prodotto associato utilizzando l&#39;origine di magazzino del sito Web principale (qtà impostata = 1).
1. Ordinare il prodotto configurabile.
1. Esegui il cron.
1. Apri il prodotto configurabile dalla vetrina e conferma che non è disponibile.
1. Apri il prodotto configurabile da [!UICONTROL Admin] e imposta **[!UICONTROL Manage Stock Option]** a *[!UICONTROL No]*.
1. Esegui il cron.
1. Spedire l&#39;ordine e aggiungere la quantità al prodotto semplice rendendolo disponibile.
1. Esegui il cron.
1. Verifica la disponibilità del prodotto nella vetrina.

<u>Risultati previsti</u>:

Il prodotto configurabile è disponibile.

<u>Risultati effettivi</u>:

Il prodotto configurabile è esaurito.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
