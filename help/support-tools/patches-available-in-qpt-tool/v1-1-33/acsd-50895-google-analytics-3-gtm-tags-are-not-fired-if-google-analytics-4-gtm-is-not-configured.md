---
title: '"ACSD-50895: [!DNL Google Analytics] 3 I tag GTM non vengono attivati se [!DNL Google Analytics] 4 GTM non è configurato'''
description: Applicare la patch ACSD-50895 per risolvere il problema Adobe Commerce in cui [!DNL Google Analytics] 3 I tag GTM non vengono attivati se [!DNL Google Analytics] 4 GTM non è configurato.
role: Admin
exl-id: da48f6f1-a68b-4a9c-a79a-d7bd01b65dc2
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-50895 [!DNL Google Analytics] 3 I tag GTM non vengono attivati se [!DNL Google Analytics] 4 GTM non è configurato

La patch ACSD-50895 risolve il problema dove [!DNL Google Analytics] 3 I tag GTM non vengono attivati se [!DNL Google Analytics] 4 GTM non è configurato. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33. L’ID della patch è ACSD-50895. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

[!DNL Google Analytics] 3 I tag GTM non vengono attivati se [!DNL Google Analytics] 4 GTM non è configurato.

<u>Passaggi da riprodurre</u>:

1. Accedi come utente amministratore.
1. Abilita **[!DNL Google Analytics 3]** e **[!DNL Google Tag Manager]** in **Amministratore** > **Archivia** > **Configurazione** > **Vendite** > **API GOOGLE** > **Google Analytics**.
1. Non attivare **[!DNL Google Analytics 4]** e **[!DNL Google Tag Manager]**.
1. Apri la pagina del prodotto sullo Storefront.

<u>Risultati previsti</u>:

I tag GTM vengono attivati solo quando **[!DNL Google Analytics]** 3 GTM è attivato.

<u>Risultati effettivi</u>:

I tag GTM non vengono attivati quando **[!DNL Google Analytics]** 4 GTM è disabilitato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
