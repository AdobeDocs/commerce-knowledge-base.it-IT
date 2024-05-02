---
title: "ACSD-47054: anteprima del contenuto lenta quando tutti gli store si reindicizzano"
description: Applica la patch ACSD-47054 per risolvere il problema di Adobe Commerce, in cui il caricamento della pagina di anteprima è lento a causa della reindicizzazione di tutti gli store.
feature: Page Content
role: Admin, Developer
exl-id: 4dc61f78-7038-48ab-a2d3-9b05cf0c9b5c
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-47054: anteprima del contenuto lenta quando tutti gli store si reindicizzano

La patch ACSD-47054 risolve il problema relativo al tempo di caricamento di un’anteprima della gestione temporanea dei contenuti, quando sono presenti molti store. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.37. L’ID della patch è ACSD-47054. Il problema è stato risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione): 2.4.2-p2, 2.4.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione): 2.4.2 - 2.4.5-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il caricamento della pagina di anteprima richiede molto tempo a causa della reindicizzazione di tutti gli store.

<u>Passaggi da riprodurre</u>:

1. Accedi a Amministrazione Commerce.
1. Crea qualsiasi aggiornamento pianificato.
1. Vai a **[!UICONTROL Content]** > **[!UICONTROL Dashboard]**.
1. Visualizza l’anteprima dell’aggiornamento pianificato.
1. Apri qualsiasi categoria.

<u>Risultati previsti</u>:

La pagina di anteprima viene caricata entro un tempo accettabile.

<u>Risultati effettivi</u>:

L’anteprima della gestione temporanea dei contenuti richiede molto tempo.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
