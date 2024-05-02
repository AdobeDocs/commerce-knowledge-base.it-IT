---
title: "MDVA-39181: le regole di prodotto correlate mostrano i prodotti della categoria non definiti nella regola"
description: La patch MDVA-39181 risolve il problema che causa la visualizzazione di prodotti di una categoria non definita nella regola da parte di regole di prodotto correlate. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10. L'ID della patch è MDVA-39181. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: b6364d1c-2480-483a-9a83-ac91feeb14b9
feature: Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-39181: le regole di prodotto correlate mostrano i prodotti della categoria non definiti nella regola

La patch MDVA-39181 risolve il problema che causa la visualizzazione di prodotti di una categoria non definita nella regola da parte di regole di prodotto correlate. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10. L&#39;ID della patch è MDVA-39181. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le regole di prodotto correlate mostrano i prodotti di categorie non definite nella regola.

<u>Prerequisiti</u>:

Installa i dati di esempio.

<u>Passaggi da riprodurre</u>:

1. Creare un marchio di attributi e aggiungerlo al **Set di attributi top**.
1. Scegli **Josie**, **Augusta**, e **Ingrid** giacche da aggiungere al Brand Kitty da **Donne** > **In alto** > **Categoria giacche**.
1. Scegli **Beaumont**, **Hyperion**, e **Kenobi** giacche da aggiungere al Brand Kitty da **Uomini** > **In alto** > **Categoria giacca**.
1. Crea un prodotto correlato con:

   ```markdown
   Apply To: Related Products
   Customer Segments: All
   ```

   * Prodotti corrispondenti:

   ```markdown
   If ALL of these conditions are TRUE
     Category is {}
     Brand is {}
   ```

   * Prodotti da visualizzare:

   ```markdown
   If ALL of these conditions are TRUE
      Product Category is the same as Matched Product Category
      Product brand is Matched Product Brand
   ```

1. Apri SKU WJ04 dal front-end e controlla i prodotti correlati.
1. Aggiorna l&#39;ID categoria da **Donne** > **In alto** > **Giacche** nel caso sia diverso da questo.

<u>Risultati previsti</u>:

Solo i prodotti della stessa marca e della stessa categoria secondaria sono visualizzati nei prodotti correlati.

<u>Risultati effettivi</u>:

I prodotti correlati sono mostrati dello stesso marchio ma da una categoria padre casuale.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
