---
title: "ACSD-50478: problema JS per l’azione di rollback nella griglia dei backup e nel comando di rollback del database"
description: Applica la patch ACSD-50478 per risolvere il problema JS per l’azione di rollback nella griglia dei backup e il comando di rollback del database per un caso in cui il dump del database contiene trigger e un comando SQL *delimiter*.
exl-id: 8b516705-29be-462e-b3ec-3a339b6e8006
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-50478: problema JS per l’azione di rollback nella griglia dei backup e nel comando di rollback del database

La patch ACSD-50478 risolve il problema JS per l&#39;azione di rollback nella griglia dei backup e il comando di rollback del database per un caso in cui il dump del database contiene trigger e un comando SQL *delimiter*. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33. L’ID della patch è ACSD-50478. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.4-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Problema JS per l&#39;azione di rollback nella griglia Backup e il comando di rollback del database per un caso in cui il dump del database contiene trigger e un comando SQL *delimiter*.

<u>Passaggi da riprodurre</u>:

1. Impostare gli indicizzatori sulla modalità [!UICONTROL Update on Schedule] in modo che i trigger vengano creati nel database.
1. Abilita la funzionalità di backup dalla riga di comando:

   `bin/magento config:set system/backup/functionality_enabled 1`

1. Vai a **Sistema** > **Strumenti** > **Backup** e genera un backup del database.
1. Apri la console del browser; verrà visualizzato il seguente errore:

   ```
   Uncaught SyntaxError: Unexpected token '&' (at (index):606:32)
   
   function eventListener8jtGaqtgG2 () {
   
           return backup.rollback(&#039;db&#039;, &#039;1678391644&#039;);
   ```

1. Provare a importare il database dalla riga di comando:

   `bin/magento setup:rollback --db-file="<filename>"`

1. Viene visualizzato il seguente errore:

   ```
   Syntax error or access violation: 1064 You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'delimiter' at line 1, query was: delimiter ;;
   ```

<u>Risultati previsti</u>:

Il ripristino del database è stato eseguito correttamente sia dalla riga di comando Admin che da quella.

<u>Risultati effettivi</u>:

Sono stati osservati gli errori indicati nei passaggi 4 e 6.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
