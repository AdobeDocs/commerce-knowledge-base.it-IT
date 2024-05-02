---
title: "ACSD-54007: errore di _ambito chiave di array non definito durante l’importazione dei dati del cliente"
description: Applica la patch ACSD-54007 per risolvere il problema di Adobe Commerce, se durante l’importazione dei dati dei clienti viene visualizzato un errore di _ambito chiave array non definita.
feature: Data Import/Export
role: Admin, Developer
exl-id: b14a14fd-5021-460f-8ca9-c9845859df97
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# ACSD-54007: errore di _ambito chiave di array non definito durante l’importazione dei dati del cliente

La patch ACSD-54007 risolve il problema in caso di *_Ambito chiave di array non definito* errore durante l’importazione dei dati del cliente. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40. L’ID della patch è ACSD-54007. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Durante l’importazione dei dati dei clienti, viene visualizzata una *_Ambito chiave di array non definito* errore.

<u>Passaggi da riprodurre</u>:

1. Vai a Amministrazione Commerce > **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** >  **[!UICONTROL Import]**, impostato **[!UICONTROL Entity Type]** a **[!UICONTROL Stock Sources]** e importare il file csv di origine delle scorte (che contiene codice sorgente, SKU, quantità e stato).
1. Scegliere Clienti e indirizzi (file singolo) e provare a importare il file CSV contenente i dettagli dell&#39;indirizzo del cliente.

<u>Risultati previsti</u>:

Non ci sono errori.

<u>Risultati effettivi</u>:

Viene visualizzato il seguente errore:  *Avvertenza: chiave di array &quot;_scope&quot; non definita in /var/www/html/vendor/magento/module-customer-import-export/Model/ResourceModel/Import/CustomerComposite/Data.php alla riga 84*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
