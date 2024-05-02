---
title: "ACSD-48212: l’importazione del prodotto assegna il prodotto a un’origine errata"
description: Applica la patch ACSD-48212 per risolvere il problema di Adobe Commerce, a causa del quale l’importazione del prodotto assegna il prodotto alla sorgente errata.
exl-id: b3426f62-f73a-4b76-8e0e-544a9133720f
feature: Admin Workspace, Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-48212: l’importazione del prodotto assegna il prodotto a un’origine errata

La patch ACSD-48212 risolve il problema che causa l’importazione del prodotto, il quale viene assegnato all’origine errata. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26. L’ID della patch è ACSD-48212. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’importazione del prodotto assegna il prodotto all’origine errata.

<u>Passaggi da riprodurre</u>:

1. Crea un&#39;origine magazzino secondaria.
1. Crea un prodotto solo con l&#39;origine di magazzino predefinita.
1. Esporta il prodotto.
1. Esegui `bin/magento cron:run`.
1. Apri **[!UICONTROL Catalog]** > **[!UICONTROL Prdoucts]**.
1. Seleziona il prodotto dalla griglia.
1. Annullare l&#39;assegnazione del materiale mediante *[!UICONTROL mass action]* menu.
1. Esegui `bin/magento cron:run`.
1. Assegnare l&#39;origine secondaria utilizzando *[!UICONTROL mass action]* menu.
1. Esegui `bin/magento cron:run`.
1. Elimina il prodotto utilizzando *[!UICONTROL mass action]* menu.
1. Esegui `bin/magento cron:run`.
1. Importa il prodotto utilizzando il file CSV esportato in precedenza.
1. Controllare l&#39;assegnazione di origine.

<u>Risultati previsti</u>:

Il prodotto viene assegnato solo all&#39;origine predefinita.

<u>Risultati effettivi</u>:

Il prodotto viene assegnato sia all&#39;origine predefinita che a quella secondaria.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
