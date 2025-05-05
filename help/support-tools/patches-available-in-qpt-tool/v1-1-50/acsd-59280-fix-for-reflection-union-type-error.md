---
title: 'Errore "ACSD-59280: &grave;ReflectionUnionType::getName()&grave; nelle installazioni 2.4.4-pX"'
description: Applica la patch ACSD-59280 per risolvere il problema di Adobe Commerce, in cui si verifica l’errore "call to undefined method ReflectionUnionType::getName()" durante l’installazione delle versioni 2.4.4-pX.
feature: Install, Upgrade
role: Admin, Developer
source-git-commit: a7a42520c6c7d74e995d104271afa2b15b537de7
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# ACSD-59280: errore `ReflectionUnionType::getName()` nelle installazioni 2.4.4-pX

La patch ACSD-59280 risolve il problema in cui si verifica l&#39;errore `call to undefined method ReflectionUnionType::getName()` durante l&#39;installazione delle versioni 2.4.4-pX. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50. L’ID della patch è ACSD-59280. Il problema è stato risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p8

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.4-p10

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Errore `ReflectionUnionType::getName()` durante l&#39;installazione di 2.4.4-pX.

<u>Passaggi da riprodurre</u>:

Eseguire una nuova installazione utilizzando *[!UICONTROL Composer]*.

<u>Risultati previsti</u>:

Il processo di installazione viene completato senza errori.

<u>Risultati effettivi</u>:

Durante il processo `setup:upgrade` viene visualizzato il seguente errore:

`Call to undefined method ReflectionUnionType::getName()`

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
