---
title: "MDVA-34695: prodotti e categorie non visualizzati"
description: La patch MDVA-34695 risolve il problema che impedisce la visualizzazione di prodotti e categorie nella griglia delle categorie in Admin. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18. L'ID della patch è MDVA-34695. Il problema è stato risolto nella versione 2.4.3 di Adobe Commerce.
exl-id: 0c2e50c1-648b-480a-a768-72af721950d8
feature: Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# MDVA-34695: prodotti e categorie non visualizzati

La patch MDVA-34695 risolve il problema che impedisce la visualizzazione di prodotti e categorie nella griglia delle categorie in Admin. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18. L&#39;ID della patch è MDVA-34695. Il problema è stato risolto nella versione 2.4.3 di Adobe Commerce.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.4

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce on-premise e Adobe Commerce sull’infrastruttura cloud 2.3.0-2.4.0-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Valori negativi per `children_count` dopo aver eliminato le categorie, vengono visualizzati nel database.

<u>Passaggi da riprodurre</u>:

1. Accedi al backend di amministrazione.
1. Accedi a **Catalog > Categories**.
1. Clic **Aggiungi sottocategoria**.
1. Imposta **nome categoria** = *Elemento padre 1*, quindi Salva.
1. Clic **Aggiungi sottocategoria**.
1. Imposta **nome categoria** = *Figlio 1*, quindi Salva.
1. Clic **Aggiungi sottocategoria**.
1. Imposta **nome categoria** = *Figlio 2*, quindi Salva.
1. Clic **Aggiungi sottocategoria**.
1. Imposta **nome categoria** = *Figlio 3*, quindi Salva. A questo punto, questa categoria deve avere un livello = *5*.
1. Fai clic sul pulsante **Figlio 1** categoria.
1. Elimina la categoria.

<u>Risultati previsti</u>:

La griglia delle categorie mostra i prodotti e le categorie, come previsto.

<u>Risultati effettivi</u>:

La griglia delle categorie è vuota. Controlla la `catalog_category_entity` nel database. Tieni presente che `children_count` è diventato negativo.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sezione.
