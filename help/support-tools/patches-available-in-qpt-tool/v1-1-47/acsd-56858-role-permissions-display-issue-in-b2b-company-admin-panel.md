---
title: "ACSD-56858: discrepanza nelle autorizzazioni del ruolo nell’amministratore dell’azienda B2B"
description: Applica la patch ACSD-56858 per risolvere il problema di Adobe Commerce, in cui le autorizzazioni dei ruoli non vengono visualizzate correttamente per un amministratore aziendale con restrizioni nell’ambiente B2B.
feature: Companies, B2B, Roles/Permissions
role: Admin, Developer
exl-id: d446f815-78bf-42ec-bc2b-a5934b15b416
source-git-commit: 4bf5deb1115705560acc8410441219943329c1a4
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# ACSD-56858: discrepanza nelle autorizzazioni dei ruoli nell’amministratore dell’azienda B2B

La patch ACSD-56858 risolve il problema relativo alla visualizzazione errata delle autorizzazioni dei ruoli per un amministratore aziendale con restrizioni nell’ambiente B2B. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.47. L’ID della patch è ACSD-56858. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.6-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le autorizzazioni per il ruolo di amministratore di un’azienda con restrizioni nell’ambiente B2B non vengono visualizzate in modo corretto.

<u>Passaggi da riprodurre</u>:

1. Per prima cosa, imposta una società, aggiungendo un amministratore della società e gli utenti della società.
1. Accedi allo storefront come amministratore aziendale e crea vari ruoli per utenti diversi.
1. Assegna questi ruoli in base alle esigenze, ad esempio limitando l’accesso ad alcune attività e consentendo l’accesso completo ad altre.
1. Assegna questi ruoli con accesso completo a un utente diverso dall’amministratore della società.
1. Accedi a un utente amministratore non aziendale, ad esempio company_manager.
1. Accedi a **[!UICONTROL Roles and permission]** e modificare il ruolo.
1. Tieni presente che le autorizzazioni visualizzate non corrispondono alle autorizzazioni impostate nel database dell’azienda per tale ID ruolo.

<u>Risultati previsti</u>:

I ruoli e le autorizzazioni vengono visualizzati correttamente per l’utente amministratore non aziendale.

<u>Risultati effettivi</u>:

I ruoli non vengono visualizzati correttamente per l’utente amministratore non aziendale in base ai record del database nella tabella delle autorizzazioni.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
