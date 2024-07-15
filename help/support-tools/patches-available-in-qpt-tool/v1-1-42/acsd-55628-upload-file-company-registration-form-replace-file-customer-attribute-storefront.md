---
title: "ACSD-55628: caricamento del file nel modulo di registrazione della società; sostituzione del file per l’attributo del cliente nella vetrina"
description: Applica la patch ACSD-55628 per risolvere il problema di Adobe Commerce relativo al caricamento di un file nel modulo di registrazione della società e alla sostituzione di un file per un attributo del cliente nella vetrina.
feature: Storefront, Attributes, B2B, Customers
role: Admin, Developer
exl-id: ca85b459-f72b-4663-85af-1f793935fe7e
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-55628: caricamento del file nel modulo di registrazione della società; sostituzione del file per l&#39;attributo del cliente nella vetrina

>[!NOTE]
>
>Questa patch sostituisce [ACSD-51240](/help/support-tools/patches-available-in-qpt-tool/v1-1-33/acsd-51240-uploaded-file-missing-while-registering-via-company-registration-form.md).

La patch ACSD-55628 risolve il problema relativo al caricamento di un file nel modulo di registrazione della società e alla sostituzione di un file per un attributo del cliente nella vetrina. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42. L’ID della patch è ACSD-55628. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p2 &lt; 2.4.5 e 2.4.5-p1 &lt; 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Impossibile sostituire un file per un attributo del cliente nella vetrina.

<u>Passaggi da riprodurre</u>:

1. Crea un nuovo attributo cliente con i seguenti valori:

   * *[!UICONTROL Input Type]*: *[!UICONTROL File (Attachment)]*
   * *[!UICONTROL Show on Storefront]*: *Sì*
   * *[!UICONTROL Forms to Use In]*: *tutte le opzioni disponibili*

1. Accedi come cliente nella vetrina e apri **[!UICONTROL My Account]** > **[!UICONTROL Account Information]**.
1. Carica una nuova immagine e salva.
1. Aggiorna la pagina. Elimina la vecchia immagine e caricane una nuova. Salva le modifiche.

<u>Risultati previsti</u>:

La nuova immagine viene salvata.

<u>Risultati effettivi</u>:

La vecchia immagine viene ancora visualizzata.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
