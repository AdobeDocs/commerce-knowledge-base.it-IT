---
title: "ACSD-54342: messaggio di errore durante l’importazione di un file CSV senza dati validi"
description: Applica la patch ACSD-54342 per risolvere il problema di Adobe Commerce, in cui si verifica un messaggio di errore non corretto durante l’importazione di un file CSV senza dati validi.
feature: Roles/Permissions
role: Admin, Developer
exl-id: 7f443ad8-c4b7-4294-b38f-9861e221bef2
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# ACSD-54342: messaggio di errore durante l’importazione di un file CSV senza dati validi

La patch ACSD-54342 risolve il problema relativo alla visualizzazione di un messaggio di errore non corretto durante l&#39;importazione di un file CSV senza dati validi. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.39. L’ID della patch è ACSD-54342. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Viene visualizzato un messaggio di errore non corretto quando si importa un file CSV senza dati validi.

<u>Passaggi da riprodurre</u>:

1. Creare un file di importazione con solo dati non validi (ad esempio: [!DNL SKUs] che non esistono, campi indirizzo cliente non validi o indirizzi e-mail cliente non validi).
1. Importa il file, selezionando per ignorare gli errori di convalida.

<u>Risultati previsti</u>:

La convalida non riesce con `There are no valid rows to import` messaggio.

<u>Risultati effettivi</u>:

La convalida viene superata, ma l&#39;importazione non riesce con il messaggio `Error in data structure: values are mixed`.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
