---
title: "ACSD-50817: ottimizza l’esecuzione del processo cron sales_clean_quote per velocizzare"
description: Applica la patch ACSD-50817 per ottimizzare il processo cron "sales_clean_quote" in modo che venga eseguito più rapidamente aggiungendo un indice composito nelle colonne "store_id" e "updated_at" della tabella delle quotazioni.
exl-id: b08b12ff-37ac-4a7d-bce2-2a27e4f916f0
feature: Quotes
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-50817: Ottimizza il processo cron `sales_clean_quotes` per eseguire più velocemente

La patch ACSD-50817 ottimizza il processo cron `sales_clean_quotes` per velocizzare l&#39;esecuzione aggiungendo un indice composito `store_id` e `updated_at` nella tabella delle offerte. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.31. L’ID della patch è ACSD-50817.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Processo cron `sales_clean_quotes` è troppo lento. Con questa patch, è stato ottimizzato per essere eseguito più rapidamente aggiungendo un indice composito sulla `store_id` e `updated_at` nella tabella delle offerte.

<u>Passaggi da riprodurre</u>:

1. Genera 50-80 milioni di preventivi con `updated_at` impostato come periodo &lt; 30 giorni.
1. Esegui il processo cron `sales_clean_quotes` oppure la seguente query nella tabella delle offerte:

   ```cron
   SELECT COUNT(*) FROM `quote` AS `main_table` WHERE (`store_id` = '1') AND (`updated_at` <= '2023-02-25') AND (`is_persistent` = '0')
   
   SELECT * FROM `quote` AS `main_table` WHERE (`store_id` = '1') AND (`updated_at` <= '2023-02-25') AND (`is_persistent` = '0') LIMIT 50
   ```

<u>Risultati previsti</u>

Processo Cron `sales_clean_quotes` è ottimizzato per essere eseguito più rapidamente aggiungendo un indice composito sul `store_id` e `updated_at` nella tabella delle offerte.

<u>Risultati effettivi</u>

Query troppo lenta.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
