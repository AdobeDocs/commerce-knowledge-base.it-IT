---
title: '''MDVA-21095: INSERT INTO "search_tmp..." non termina mai dopo l''aggiornamento di massa degli attributi'''
description: La patch MDVA-21095 risolve il problema quando una query "INSERT INTO" "search\_tmp..." non termina mai dopo un aggiornamento di massa dell’attributo. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20. L'ID della patch è MDVA-21095. Tieni presente che non esiste un piano corrente per risolvere questo problema nelle versioni future.
exl-id: fd599473-b49a-4f9c-a13f-612d05e43f09
feature: Attributes, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# MDVA-21095: INSERT INTO &quot;search_tmp...&quot; non termina mai dopo l&#39;aggiornamento di massa degli attributi

La patch MDVA-21095 risolve il problema quando viene eseguita una query `INSERT INTO` &quot;search\_tmp...&quot; non termina mai dopo un aggiornamento di massa dell&#39;attributo. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20. L&#39;ID della patch è MDVA-21095. Tieni presente che non esiste un piano corrente per risolvere questo problema nelle versioni future.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.2

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.3.4-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

`INSERT INTO` &quot;search\_tmp...&quot; non termina mai dopo un aggiornamento di massa dell&#39;attributo.

<u>Passaggio da riprodurre</u>:

Eseguire un aggiornamento dei valori degli attributi di massa con circa 30.000 elementi.

<u>Risultati previsti</u>:

Il processo di reindicizzazione viene completato normalmente, come previsto.

<u>Risultati effettivi</u>:

Il processo di reindicizzazione è stato completato, ma sono state eseguite molte query `INSERT INTO` &quot;search\_tmp...&quot; inizia finché il server non raggiunge `pm.max_children` Il valore di parametro e PHP-fpm muoiono, e questi si ripetono costantemente anche dopo il riavvio di MySQL e l&#39;arresto del processo.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
