---
title: "ACSD-58375: la chiave API YouTube configurata in modo errato causa un errore durante l’aggiunta di video a livello di visualizzazione archivio"
description: Applica la patch ACSD-58375 per risolvere il problema di Adobe Commerce, se la configurazione errata della chiave API di YouTube causa un errore durante l’aggiunta di un video YouTube a livello di visualizzazione archivio.
feature: Catalog Management, Configuration
role: Admin, Developer
source-git-commit: 1887a74b0c5545f9213f54602c58de7028d1ad72
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-58735: la chiave API YouTube non configurata correttamente causa un errore durante l’aggiunta di video a livello di visualizzazione archivio

La patch ACSD-58735 risolve il problema se la configurazione errata della chiave API di YouTube causa un errore durante l’aggiunta di un video YouTube a livello di visualizzazione archivio. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49. L’ID della patch è ACSD-58735. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.6-p7

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Una configurazione errata della chiave API YouTube causa un errore durante l’aggiunta di un video YouTube a livello di visualizzazione store.

<u>Passaggi da riprodurre</u>:

1. Vai a Amministrazione > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Video]**.
1. Cambia il livello *Ambito* in *[!UICONTROL Main Website]*.
1. Aggiungi la chiave API di YouTube.
1. Vai a **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Selezionare un prodotto e scorrere fino a *[!UICONTROL Images and Video]*. Fare clic su **[!UICONTROL Add Video]**.
1. Copia un collegamento video YouTube e incollalo nel campo collegamento video. Esci dal campo.

<u>Risultati previsti</u>:

La chiave API di YouTube ha un ambito globale ed è nascosta a livello di sito web.

<u>Risultati effettivi</u>:

Viene generato il seguente errore: *Il video non viene visualizzato per il seguente motivo: Chiave API non valida. Passare una chiave API valida*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
