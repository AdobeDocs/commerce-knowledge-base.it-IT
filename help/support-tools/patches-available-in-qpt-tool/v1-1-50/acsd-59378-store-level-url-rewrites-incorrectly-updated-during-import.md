---
title: "ACSD-59378: il livello di archivio [!DNL URL] riscrive non correttamente aggiornato durante l'importazione"
description: Applica la patch ACSD-59378 per risolvere il problema di Adobe Commerce per cui le riscritture a livello di archivio [!DNL URL] non vengono aggiornate correttamente durante l'importazione.
feature: Data Import/Export
role: Admin, Developer
source-git-commit: 3f400c3e325c3f377a5e12170b08615ebeadbcd1
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---


# ACSD-59378: riscritture a livello di archivio [!DNL URL] non correttamente aggiornate durante l&#39;importazione

La patch ACSD-59378 risolve il problema relativo all&#39;aggiornamento errato delle riscritture a livello di archivio [!DNL URL] durante l&#39;importazione. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50. L’ID della patch è ACSD-59378. Tieni presente che questo problema è stato risolto in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p5

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.5x (tutte le versioni di 2.4.5)

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le riscritture a livello di archivio [!DNL URL] non vengono aggiornate correttamente durante l&#39;importazione.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto con `url_key = key_default` nell&#39;ambito **Tutte le visualizzazioni dello store**.
1. Imposta `url_key = key_store` nell&#39;ambito **Visualizzazione archivio predefinita**.
1. Esporta il prodotto.
1. Importa un file [!DNL CSV] per questo prodotto con i seguenti dati:
   * La colonna `store_view_code` è impostata su *vuota* in modo che venga applicata all&#39;ambito **Tutte le visualizzazioni archivio**.
   * `url_key` è impostato sulla chiave predefinita *`key_default`*.

<u>Risultati previsti</u>:

Le riscritture di [!DNL URL] vengono rigenerate solo per le visualizzazioni archivio in cui non è presente alcun `url_key` sovrascritto (dove è applicabile l&#39;impostazione predefinita `url_key`).

<u>Risultati effettivi</u>:

`key_store` [!DNL URL] riscritture sono state eliminate, ma la riscrittura [!DNL URL] nel livello **Visualizzazione archivio predefinita** per il prodotto è ancora impostata su *`key_store`*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
