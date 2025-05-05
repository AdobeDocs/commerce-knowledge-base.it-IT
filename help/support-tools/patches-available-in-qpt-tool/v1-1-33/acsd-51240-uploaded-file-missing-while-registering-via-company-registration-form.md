---
title: 'ACSD-51240: file caricato mancante durante la registrazione tramite il modulo di registrazione della società'
description: Applica la patch ACSD-51240 per risolvere il problema di Adobe Commerce relativo alla mancanza del file caricato durante la registrazione tramite il modulo di registrazione della società.
exl-id: e5822c54-4e77-46b0-84b6-5e25c3845974
source-git-commit: e1fe8936c56f422ae591c6424d8a72621093db81
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-51240: file caricato mancante durante la registrazione tramite il modulo di registrazione della società

>[!NOTE]
>
>Questa patch è sostituita da [ACSD-55628](/help/support-tools/patches-available-in-qpt-tool/v1-1-42/acsd-55628-upload-file-company-registration-form-replace-file-customer-attribute-storefront.md).

La patch ACSD-51240 risolve il problema relativo alla mancanza del file caricato durante la registrazione tramite il modulo di registrazione della società. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33. L’ID della patch è ACSD-51240. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 &lt; 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it>). Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Problema

Il file caricato risulta mancante durante la registrazione tramite il modulo di registrazione della società.

<u>Passaggi da riprodurre</u>:

1. Imposta **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B >Company]** > **[!UICONTROL Enable]** = *Sì*.
1. Creare un nuovo attributo cliente di tipo **[!UICONTROL File]**, impostare **[!UICONTROL Show in StoreFront]** = *Sì* e selezionare **[!UICONTROL all forms]**.
1. Crea una nuova società sullo Storefront e carica un&#39;immagine per il nuovo attributo.
Apri l’azienda e l’utente amministratore sullo Storefront.

<u>Risultati previsti</u>:

Viene visualizzato il file caricato.

<u>Risultati effettivi</u>:

Il file caricato non viene visualizzato nella pagina dell&#39;azienda né nella pagina del cliente amministratore in [!UICONTROL Commerce Admin].

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
