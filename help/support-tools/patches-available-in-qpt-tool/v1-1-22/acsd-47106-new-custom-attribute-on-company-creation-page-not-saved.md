---
title: "ACSD-47106: impossibile salvare il nuovo attributo personalizzato nella pagina di creazione della società"
description: Applica la patch ACSD-47106 per risolvere il problema di Adobe Commerce, per cui un valore non può essere salvato in un nuovo attributo personalizzato nella pagina di creazione di una società.
exl-id: 941d6d8f-36eb-4b50-980f-e4afe6bf33df
feature: Attributes, B2B, Companies
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-47106: nuovo attributo personalizzato non salvato nella pagina di creazione della società

La patch ACSD-47106 risolve il problema che impediva il salvataggio di un valore in un nuovo attributo personalizzato nella pagina di creazione di una società. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.22. L’ID della patch è ACSD-47106. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Un valore non può essere salvato in un nuovo attributo personalizzato nella pagina di creazione di una società.

<u>Prerequisiti</u>:

* I moduli B2B sono installati.

<u>Passaggi da riprodurre</u>:

1. Vai a Amministrazione Commerce > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Customer]** > **[!UICONTROL Add New Attribute]**.
1. Crea nuovo attributo: _Prova 01_.
1. Vai a Amministrazione Commerce > **[!UICONTROL Customers]** > **[!UICONTROL Companies]** > e creare una nuova azienda con tutti i dettagli richiesti.
1. Prova ad aggiungere un valore all’attributo personalizzato _Prova 01_.
1. Prova ad aggiornare il valore dell’attributo personalizzato _Prova 01_.

<u>Risultati previsti</u>:

Le modifiche vengono salvate.

<u>Risultati effettivi</u>:

Le modifiche non vengono salvate.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
