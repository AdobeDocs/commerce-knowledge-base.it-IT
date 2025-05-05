---
title: '"ACSD-46938: problemi di prestazioni con i trigger del database durante "setup:upgrade""'
description: Applica la patch ACSD-46938 per risolvere il problema di Adobe Commerce, in cui il comando "setup:upgrade" cambia la modalità dell’indicizzatore da pianificazione a salvataggio, causando un significativo rallentamento delle prestazioni.
feature: Upgrade
role: Admin, Developer
source-git-commit: cbd16ac7c6d6d7a4e3786880409475a10964c070
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-46938: problemi di prestazioni con i trigger del database durante `setup:upgrade`

La patch di ACSD-46938 risolve il problema che causa un rallentamento significativo delle prestazioni, causato dalla modifica della modalità di indicizzazione da pianificazione a salvataggio da parte del comando `setup:upgrade`. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50. L’ID della patch è ACSD-46938. Il problema è stato risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.5-p9

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Peggioramento delle prestazioni durante la ricreazione del trigger del database in `setup:upgrade`.

<u>Passaggi da riprodurre</u>:

1. Crea un catalogo di grandi dimensioni con molti prodotti e categorie.
1. Accedere a [!UICONTROL Admin].
1. Imposta tutti gli indicizzatori sulla modalità [!UICONTROL Update By Schedule].
1. Apri qualsiasi prodotto.
1. Aggiornalo. Ad esempio, assegna una nuova categoria.
1. Fare clic su [!UICONTROL Save].
1. Eseguire `bin/magento setup:upgrade` e `bin/magento cron:run` comandi in parallelo.

<u>Risultati previsti</u>:

Il tempo di esecuzione del comando `bin/magento setup:upgrade` aumenta in modo significativo quando il comando `bin/magento cron:run` viene eseguito contemporaneamente.

<u>Risultati effettivi</u>:

Il tempo di esecuzione del comando non aumenta.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
