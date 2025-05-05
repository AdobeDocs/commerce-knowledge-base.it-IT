---
title: 'ACSD-54007: errore di _ambito chiave di array non definito durante l’importazione dei dati del cliente'
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

La patch ACSD-54007 risolve il problema relativo all&#39;errore *Chiave di array non definita _scope* durante l&#39;importazione dei dati del cliente. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40. L’ID della patch è ACSD-54007. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Durante l&#39;importazione dei dati del cliente, viene visualizzato un errore *di chiave di array non definita _scope*.

<u>Passaggi da riprodurre</u>:

1. Vai a Amministrazione Commerce > **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]**, imposta **[!UICONTROL Entity Type]** su **[!UICONTROL Stock Sources]** e importa il file csv di origine delle scorte (che contiene il codice sorgente, lo SKU, la quantità e lo stato).
1. Scegliere Clienti e indirizzi (file singolo) e provare a importare il file CSV contenente i dettagli dell&#39;indirizzo del cliente.

<u>Risultati previsti</u>:

Non ci sono errori.

<u>Risultati effettivi</u>:

Errore: *Avviso: chiave di matrice &quot;_scope&quot; non definita in /var/www/html/vendor/magento/module-customer-import-export/Model/ResourceModel/Import/CustomerComposite/Data.php alla riga 84*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
