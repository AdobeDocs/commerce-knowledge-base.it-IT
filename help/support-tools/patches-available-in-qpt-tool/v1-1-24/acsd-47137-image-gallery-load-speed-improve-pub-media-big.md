---
title: '"ACSD-47137: migliorare la velocità di caricamento della galleria di immagini con la cartella ''pub/media'' grande'
description: Applica la patch ACSD-47137 per migliorare la velocità di caricamento della galleria di immagini quando la cartella "pub/media" è molto grande.
exl-id: 43268909-6845-4d1d-b6b8-4ae0ce40fd5e
feature: Cache, Catalog Management, Categories, Media
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-47137: migliora la velocità di caricamento della galleria di immagini quando `pub/media` cartella grande

La patch ACSD-47137 migliora la velocità di caricamento della galleria di immagini quando `pub/media` La cartella è molto grande. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24. L’ID della patch è ACSD-47137. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La velocità di caricamento della galleria di immagini è lenta quando `pub/media` La cartella è molto grande.

<u>Passaggi da riprodurre</u>:

1. Vai a Amministrazione di Adobe Commerce > **[!UICONTROL STORES]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery]** > **[!UICONTROL Enable Old Media Gallery]** a _No_.
1. Pulisci la cache di configurazione.
1. Esci e accedi di nuovo come utente amministratore.
1. Nella barra laterale Amministratore, vai a **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** e seleziona la categoria principale.
1. Espandi **[!UICONTROL Content]** e fai clic su **[!UICONTROL Select from Gallery]**.

Quando si carica la pagina, Adobe Commerce invia `media_gallery/directories/gettree` richiesta di caricamento della struttura di cartelle multimediali.

<u>Risultati previsti</u>:

Il `media_gallery/directories/gettree` La richiesta deve caricare il contenuto solo dalle directory necessarie, ad eccezione del loop dell’intero elenco di percorsi dalla `pub/media/` cartella.

<u>Risultati effettivi</u>:

Il `media_gallery/directories/gettree` il caricamento della richiesta richiede molto tempo quando `pub/media/` La cartella contiene molti contenuti.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
