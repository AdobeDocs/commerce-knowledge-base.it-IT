---
title: "ACSD-51358: aggiornamenti della pianificazione mancanti"
description: Applica la patch ACSD-51358 per risolvere il problema di Adobe Commerce, in cui le modifiche all’aggiornamento pianificato senza data di fine determinano la rimozione di altri aggiornamenti pianificati sulla stessa entità.
feature: Staging
role: Admin, Developer
exl-id: 8bc4c505-9cf2-4c33-93a1-4b4d7d0dfc15
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-51358: mancano aggiornamenti della pianificazione

La patch ACSD-51358 risolve il problema che causa la rimozione di altri aggiornamenti pianificati sulla stessa entità a causa delle modifiche apportate all’aggiornamento pianificato senza data di fine. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.35. L’ID della patch è ACSD-51358. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le modifiche apportate all’aggiornamento programmato senza data di fine determinano la rimozione di altri aggiornamenti programmati sulla stessa entità.

<u>Passaggi da riprodurre</u>:

1. Creare un **[!UICONTROL scheduled update]** senza la data di fine (*aggiornamento 1*).
1. Crea nuovo **[!UICONTROL scheduled update]** con la stessa data di inizio del primo aggiornamento, ma aggiungendo il giorno successivo e la data di fine (*aggiornamento 2*).
1. Modifica **[!UICONTROL scheduled update]** creato al passaggio 1 (*aggiornamento 1*) e le modifiche di salvataggio.

<u>Risultati previsti</u>

Il (*aggiornamento 2*) deve rimanere nel **[!UICONTROL schedule update]** elenca quando (*aggiornamento 1*) è stato modificato.

<u>Risultati effettivi</u>

Il (*aggiornamento 2*) è stato rimosso dal **[!UICONTROL schedule update]** elenca quando (*aggiornamento 1*) è stato modificato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) nel [!DNL Quality Patches Tool] guida.
