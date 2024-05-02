---
title: "ACSD-53824: distribuzione non riuscita durante l’aggiornamento dell’installazione"
description: Applica la patch ACSD-53824 per risolvere il problema Adobe Commerce in cui la distribuzione non riesce durante l’aggiornamento dell’installazione
feature: Attributes, Upgrade
role: Admin, Developer
exl-id: a071745f-967f-42c8-9e20-52b248e4fefa
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# ACSD-53824: distribuzione non riuscita durante l&#39;aggiornamento dell&#39;installazione

La patch ACSD-53824 risolve il problema relativo all&#39;errore di distribuzione durante l&#39;aggiornamento dell&#39;installazione. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.38. L’ID della patch è ACSD-53824. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La distribuzione non riesce durante l&#39;aggiornamento dell&#39;installazione.

<u>Passaggi da riprodurre</u>:

1. Installare l’infrastruttura con **[!DNL MariaDB]** su Galera Cluster.
1. Imposta il `wsrep_max_ws_size` fino a *2 GB*.
1. Installa una nuova istanza di Adobe Commerce.
1. Generare gli staffaggi dal profilo di prestazioni medio:
   `php bin/magento setup:performance:generate-fixtures -s setup/performance-toolkit/profiles/ee/medium.xml`
1. Genera più di **12000** attributi a selezione multipla.
1. Quindi utilizza `Run setup: Upgrade` comando.

<u>Risultati previsti</u>:

Il `setup:upgrade` viene completato senza errori.

<u>Risultati effettivi</u>:

Il `setup:upgrade` non riesce con [!DNL MySQL] errori:

`Allowed memory size of 6442450944 bytes exhausted in ../module-catalog/Setup/Patch/Data/UpdateMultiselectAttributesBackendTypes.php`

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
