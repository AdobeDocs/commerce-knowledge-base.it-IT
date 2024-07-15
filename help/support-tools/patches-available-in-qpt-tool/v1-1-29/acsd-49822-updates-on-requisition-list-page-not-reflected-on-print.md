---
title: "ACSD-49822: gli aggiornamenti nella pagina dell'elenco richieste di acquisto non vengono riportati nell'elenco delle richieste di stampa"
description: Applicare la patch ACSD-49822 per risolvere il problema di Adobe Commerce, in cui gli aggiornamenti nella pagina dell'elenco delle richieste di acquisto non vengono riportati nell'elenco delle richieste di stampa.
exl-id: 584e3fcd-9153-41aa-8857-cf1fa41269c9
feature: Admin Workspace, B2B
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-49822: gli aggiornamenti nell&#39;elenco richieste di acquisto non vengono riportati nell&#39;elenco delle richieste di stampa

La patch di ACSD-49822 risolve il problema per cui gli aggiornamenti nella pagina dell&#39;elenco delle richieste di acquisto non vengono riportati nell&#39;elenco delle richieste di stampa. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29. L’ID della patch è ACSD-49822. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli aggiornamenti nella pagina dell&#39;elenco richieste di acquisto non vengono riportati nell&#39;elenco delle richieste di acquisto stampato.

<u>Passaggi da riprodurre</u>:

1. Abilitare l&#39;elenco delle richieste di acquisto passando a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[funzionalità B2B]**.
1. Crea un prodotto.
1. Accedere come cliente e aggiungere due prodotti all&#39;elenco delle richieste di acquisto.
1. Vai a **[!UICONTROL My Account]** > **[!UICONTROL My Requisition Lists]**.
1. Visualizzare un elenco di richieste.
1. Fai clic su **[!UICONTROL Print]** nell&#39;angolo superiore destro.
1. Chiudere la finestra di stampa e stampare la pagina dell&#39;elenco delle richieste di acquisto.
1. Eliminare un articolo nell&#39;elenco o aggiornare la quantità di un articolo e riprovare a stamparlo.
1. Nella finestra di stampa gli elementi non vengono aggiornati.
1. Chiudere la finestra di stampa.
1. Nella pagina di stampa dell&#39;elenco delle richieste di acquisto non vengono aggiornati gli articoli.

<u>Risultati previsti</u>:

L&#39;elenco da stampare viene aggiornato dopo l&#39;applicazione di eventuali modifiche.

<u>Risultati effettivi</u>:

Gli aggiornamenti non vengono visualizzati nella pagina di stampa dell&#39;elenco richieste di acquisto.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
