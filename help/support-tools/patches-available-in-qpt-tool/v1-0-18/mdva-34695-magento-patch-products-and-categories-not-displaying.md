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

La patch MDVA-34695 risolve il problema che impedisce la visualizzazione di prodotti e categorie nella griglia delle categorie in Admin. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18. L&#39;ID della patch è MDVA-34695. Il problema è stato risolto nella versione 2.4.3 di Adobe Commerce.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.4

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce on-premise e Adobe Commerce sull’infrastruttura cloud 2.3.0-2.4.0-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I valori negativi per `children_count` vengono visualizzati nel database dopo l&#39;eliminazione delle categorie.

<u>Passaggi da riprodurre</u>:

1. Accedi al backend di amministrazione.
1. Passa a **Catalogo > Categorie**.
1. Fare clic su **Aggiungi sottocategoria**.
1. Imposta **nome categoria** = *Elemento padre 1*, quindi Salva.
1. Fare clic su **Aggiungi sottocategoria**.
1. Imposta **nome categoria** = *Figlio 1*, quindi Salva.
1. Fare clic su **Aggiungi sottocategoria**.
1. Imposta **nome categoria** = *Figlio 2*, quindi Salva.
1. Fare clic su **Aggiungi sottocategoria**.
1. Imposta **nome categoria** = *Figlio 3*, quindi Salva. A questo punto, questa categoria deve avere un livello = *5*.
1. Fare clic sulla categoria **Figlio 1**.
1. Elimina la categoria.

<u>Risultati previsti</u>:

La griglia delle categorie mostra i prodotti e le categorie, come previsto.

<u>Risultati effettivi</u>:

La griglia delle categorie è vuota. Controllare la tabella `catalog_category_entity` nel database. `children_count` è diventato negativo.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
