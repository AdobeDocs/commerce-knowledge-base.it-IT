---
title: "ACSD-47669: Errore interno del server durante l’importazione di prodotti con opzioni personalizzabili"
description: Applica la patch ACSD-47669 per risolvere il problema di Adobe Commerce in caso di errore interno del server durante l’importazione di prodotti con opzioni personalizzabili.
feature: Products
role: Admin, Developer
exl-id: 14afbd71-075a-4264-8da2-dbbd93f472a1
source-git-commit: 66e56b9ba31fd2c5d3f8a330f09d8e94df77b17d
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-47669: Errore interno del server durante l’importazione di prodotti con opzioni personalizzabili

La patch ACSD-47669 risolve il problema relativo a un errore interno del server durante l’importazione del prodotto, con opzioni personalizzabili. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.38. L’ID della patch è ACSD-47669. Il problema è già risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.5-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Errore interno del server durante l’importazione di prodotti con opzioni personalizzabili.

<u>Passaggi da riprodurre</u>:

1. Crea un&#39;ulteriore visualizzazione store. Assicurati di avere 2 visualizzazioni del negozio, ad es. en, UK.
1. Create due prodotti semplici, ad esempio prod1 e prod2.
1. Prepara un file CSV che aggiunge opzioni personalizzate per entrambi i prodotti in ogni visualizzazione archivio e per l&#39;ambito **Tutte le visualizzazioni archivio**. Importa questo file CSV.
1. Prepara un altro file CSV che include due record. Il primo record deve aggiornare le opzioni personalizzate di &#39;prod1&#39; specificatamente per l&#39;ambito di visualizzazione dell&#39;archivio nel Regno Unito, mentre il secondo record deve aggiornare le opzioni personalizzate di &#39;prod2&#39; per l&#39;ambito **All Store View**. Importa questo secondo file CSV.

<u>Risultati previsti</u>:

Dovresti essere in grado di personalizzare le opzioni senza errori.

<u>Risultati effettivi</u>:

Si è verificato un errore di violazione del vincolo di integrità.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
