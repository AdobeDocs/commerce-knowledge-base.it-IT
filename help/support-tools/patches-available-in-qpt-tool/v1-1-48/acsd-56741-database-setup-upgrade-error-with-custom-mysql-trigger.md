---
title: "ACSD-56741: risoluzione dei problemi relativi agli errori di installazione del database con trigger MySQL personalizzati"
description: Applica la patch ACSD-56741 per risolvere il problema di Adobe Commerce, dove viene visualizzato un messaggio di errore *Tentativo di accedere all’offset dell’array con valore nullo* durante "setup:upgrade" a causa di un trigger MySQL personalizzato nel database non correlato all’indicizzazione e [!DNL MView].
feature: Install
role: Admin, Developer
source-git-commit: 216ce1035584e4c049029073ee0017d3616cdbd6
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-56741: Risoluzione dei problemi di installazione del database con trigger MySQL personalizzati

La patch ACSD-56741 risolve il problema relativo a un messaggio di errore *Tentativo di accedere all&#39;offset dell&#39;array su un valore di tipo null* viene visualizzato durante `setup:upgrade` a causa di un trigger MySQL personalizzato nel database non correlato all&#39;indicizzazione e [!DNL MView]. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48. L’ID della patch è ACSD-56741. Il problema è pianificato per essere risolto in Adobe Commerce 2.5.0

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Un messaggio di errore *Tentativo di accedere all&#39;offset dell&#39;array su un valore di tipo null* viene visualizzato durante `setup:upgrade` a causa di un trigger MySQL personalizzato nel database non correlato all&#39;indicizzazione e [!DNL MView].

<u>Passaggi da riprodurre</u>:

1. Esegui `php bin/magento indexer:set-mode schedule`.

   ```
   DELIMITER //
   CREATE TRIGGER trg_catalog_category_entity_before_delete_umis BEFORE DELETE ON catalog_category_entity FOR EACH ROW
       -> BEGIN
       -> UPDATE ewave_navigation_menu_item_info as nit INNER JOIN ewave_navigation_menu_category_type as ncmi ON nit.id = ncmi.menu_item_id AND ncmi.category_id = OLD.entity_id SET nit.status = 0;
       -> END //
   ```

1. Esegui `php bin/magento c:f`.
1. Esegui `php bin/magento setup:upgrade`.

<u>Risultati previsti</u>:

L&#39;aggiornamento della configurazione termina senza errori.

<u>Risultati effettivi</u>:

L&#39;aggiornamento dell&#39;installazione termina con un messaggio di errore:

*Avviso: tentativo di accesso all&#39;offset della matrice su un valore di tipo null*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
