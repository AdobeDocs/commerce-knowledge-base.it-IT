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

La patch ACSD-51892 risolve il problema di prestazioni derivante dal caricamento del `app/etc/env.php` e `app/etc/config.php` ogni volta che si accede ai valori di configurazione della distribuzione in una singola richiesta. La lettura eccessiva del file mette a dura prova il sistema, con conseguente deterioramento delle prestazioni complessive. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.33. L’ID della patch è ACSD-51892. Il problema è stato risolto in Adobe Commerce 2.4.6-p2.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Si è verificato un problema di prestazioni in cui i file di configurazione vengono caricati più volte.

<u>Passaggi da riprodurre</u>:

1. Eseguire l’implementazione o l’aggiornamento a Adobe Commerce 2.4.6 o versione successiva.
1. Controllare i registri del file system per accedere a `app/etc/env.php` e `app/etc/config.php` durante l&#39;esecuzione della distribuzione.

<u>Risultati previsti</u>:

L’implementazione ha esito positivo entro l’intervallo di tempo regolare.

<u>Risultati effettivi</u>:

* I server hanno difficoltà a rispondere a qualsiasi comando immesso. Questo comporta *Errore 503 - timeout primo byte* durante l’accesso al sito web.
* Sono presenti più voci nei file di registro con accesso a `app/etc/env.php` e `app/etc/config.php` file.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
