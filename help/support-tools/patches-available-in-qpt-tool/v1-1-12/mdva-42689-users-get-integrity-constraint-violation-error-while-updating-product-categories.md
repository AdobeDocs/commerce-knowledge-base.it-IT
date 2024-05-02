---
title: "MDVA-42689: errore di violazione del vincolo di integrità durante l'aggiornamento delle categorie di prodotto durante l'importazione"
description: La patch MDVA-42689 risolve il problema relativo all'errore di violazione del vincolo di integrità durante l'aggiornamento delle categorie di prodotti durante l'importazione. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12. L'ID della patch è MDVA-42689. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: 7beff3bb-9313-43dc-be96-e33eff52a38e
feature: Categories, Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-42689: errore di violazione del vincolo di integrità durante l&#39;aggiornamento delle categorie di prodotto durante l&#39;importazione

La patch MDVA-42689 risolve il problema relativo all&#39;errore di violazione del vincolo di integrità durante l&#39;aggiornamento delle categorie di prodotti durante l&#39;importazione. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12. L&#39;ID della patch è MDVA-42689. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Adobe Commerce genera un errore di violazione del vincolo di integrità durante l’aggiornamento delle categorie di prodotti durante l’importazione.

<u>Passaggi da riprodurre</u>:

1. Imposta due siti Web.
1. Crea sottocategorie sotto la categoria principale fino a due livelli nella pagina della categoria. Ad esempio, Categoria principale > **Ingranaggio** > **Orologi**.
1. Crea due prodotti semplici e assegna entrambi i prodotti allo stesso **Ingranaggio** > **Orologi** categoria.
1. Assegna un prodotto semplice a entrambi i siti web.
1. Salva il prodotto.
1. Prepara un file CSV per l’importazione. Dovrebbero essere presenti due record di prodotto con diverse visualizzazioni dello store. Uno dei prodotti deve appartenere a entrambe queste visualizzazioni store.
1. Ora importa il file CSV passando a **Sistema** > **Importa** > **Tipo di entità** (Prodotti).

<u>Risultati previsti</u>:

Il file CSV viene importato senza errori.

<u>Risultati effettivi</u>:

Adobe Commerce genera il seguente errore:

```SQL
SQLSTATE[23000]: Integrity constraint violation: 1062 Duplicate entry '1302' for key 'PRIMARY', query was: INSERT INTO `catalog_url_rewrite_product_category` (`url_rewrite_id`,`category_id`,`product_id`) VALUES (?, ?, ?), (?, ?, ?), (?, ?, ?)
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
