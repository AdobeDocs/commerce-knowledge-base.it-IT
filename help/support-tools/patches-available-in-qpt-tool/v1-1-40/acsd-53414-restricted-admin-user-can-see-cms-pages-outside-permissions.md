---
title: 'ACSD-53414: gli utenti amministratori con restrizioni possono visualizzare le pagine CMS al di fuori del proprio ambito di autorizzazioni'
description: Applica la patch ACSD-53414 per risolvere il problema di Adobe Commerce, per cui un utente amministratore con restrizioni può visualizzare le pagine CMS al di fuori del proprio ambito di autorizzazioni.
feature: CMS
role: Admin, Developer
exl-id: f8540d52-a3bb-49bb-8868-7b1db03e571b
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-53414: gli utenti amministratori con restrizioni possono visualizzare le pagine CMS al di fuori del proprio ambito di autorizzazioni

La patch ACSD-53414 risolve il problema per cui un utente amministratore con restrizioni può visualizzare le pagine CMS al di fuori del proprio ambito di autorizzazioni. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40. L’ID della patch è ACSD-53414. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli utenti amministratori con restrizioni possono visualizzare le pagine CMS oltre l’ambito delle autorizzazioni.

<u>Passaggi da riprodurre</u>:

1. Creare un nuovo sito Web (sub_website), store (sub_store) e storeview (sub_storeview).
1. Crea un ruolo sub_expert, che consenta l’ambito di sub_website e sub_store. Assegnare solo le seguenti autorizzazioni: [!UICONTROL Dashboard] e [!UICONTROL Pages].
1. Crea un nuovo utente amministratore e assegnalo al ruolo sub_expert.
1. Assegna le seguenti pagine CSM a sub_storeview e storeview predefinito.

   * [!UICONTROL 404 Not Found] > Sottostoreview
   * [!UICONTROL 503 Service Unavailable] > Visualizzazione archivio predefinita

1. Accedi all’amministratore utilizzando l’utente amministratore creato nel passaggio 3.
1. Controlla la griglia della pagina di CMS.

<u>Risultati previsti</u>:

La pagina *[!UICONTROL 503 Service Unavailable]* non è visibile all&#39;amministratore Web.

<u>Risultati effettivi</u>:

*[!UICONTROL 503 Service Unavailable]* è visibile all&#39;amministratore Web.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
