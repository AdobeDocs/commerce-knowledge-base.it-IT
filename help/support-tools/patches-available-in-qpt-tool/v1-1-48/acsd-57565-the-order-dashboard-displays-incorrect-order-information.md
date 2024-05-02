---
title: "ACSD-57565: il dashboard dell’ordine visualizza informazioni sull’ordine non corrette"
description: Applica la patch ACSD-57565 per risolvere il problema di Adobe Commerce, a causa del quale il dashboard degli ordini visualizza informazioni di ordine errate fino all’aggiornamento del periodo di tempo.
feature: Roles/Permissions
role: Admin, Developer
exl-id: 5b292fef-23f6-479f-bf76-adad53d30cf4
source-git-commit: fdf6e6e85f903a26a7b44674937ccf88ee769d06
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-57565: il dashboard degli ordini visualizza informazioni sugli ordini errate

La patch di ACSD-57565 risolve il problema relativo alla visualizzazione di informazioni di ordine non corrette nel dashboard degli ordini fino all&#39;aggiornamento del periodo di tempo. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.48. L’ID della patch è ACSD-57565. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch

## Problema

Nel dashboard degli ordini vengono visualizzate informazioni di ordine non corrette.

<u>Passaggi da riprodurre</u>:

1. Abilita **[!UICONTROL dashboard charts]**.
1. Creare un ordine e fatturarlo.
1. Attendi almeno 24 ore dopo l’ora di creazione dell’ordine.
1. Controlla la **[!UICONTROL dashboard chart]** dati.
1. Prendere nota del conteggio completo degli ordini.
1. Modifica l’ora in *mese corrente*, quindi riportarlo a *oggi*.

<u>Risultati previsti</u>:

Il grafico del dashboard deve mostrare continuamente le statistiche corrette.

<u>Risultati effettivi</u>:

Il grafico del dashboard mostra statistiche non corrette al primo caricamento. Le statistiche accurate del grafico vengono aggiornate dopo il periodo di tempo.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
