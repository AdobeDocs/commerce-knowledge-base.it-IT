---
title: "ACSD-51892: problema di prestazioni in cui i file di configurazione vengono caricati più volte"
description: Applica la patch ACSD-51892 per risolvere il problema di prestazioni di Adobe Commerce, in cui i file di configurazione vengono caricati più volte durante la distribuzione.
feature: Observability
role: Admin
exl-id: 397343df-360f-43c4-bcef-be5f0da5aeef
source-git-commit: 97734799a39f41d0d6441379e21608fa5fcd1d4c
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-51892: problema di prestazioni in cui i file di configurazione vengono caricati più volte

La patch ACSD-51892 risolve il problema di prestazioni derivante dal caricamento dei file `app/etc/env.php` e `app/etc/config.php` ogni volta che si accede ai valori di configurazione della distribuzione in una singola richiesta. La lettura eccessiva del file mette a dura prova il sistema, con conseguente deterioramento delle prestazioni complessive. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.33. L’ID della patch è ACSD-51892. Il problema è stato risolto in Adobe Commerce 2.4.6-p2.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Si è verificato un problema di prestazioni in cui i file di configurazione vengono caricati più volte.

<u>Passaggi da riprodurre</u>:

1. Eseguire l’implementazione o l’aggiornamento a Adobe Commerce 2.4.6 o versione successiva.
1. Controllare i registri del file system per l&#39;accesso ai file `app/etc/env.php` e `app/etc/config.php` mentre la distribuzione è in esecuzione.

<u>Risultati previsti</u>:

L’implementazione ha esito positivo entro l’intervallo di tempo regolare.

<u>Risultati effettivi</u>:

* I server hanno difficoltà a rispondere a qualsiasi comando immesso. Ciò causa *Errore 503, timeout primo byte*, durante l&#39;accesso al sito Web.
* Sono presenti più voci nei file di registro con accesso a `app/etc/env.php` e `app/etc/config.php` file.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
