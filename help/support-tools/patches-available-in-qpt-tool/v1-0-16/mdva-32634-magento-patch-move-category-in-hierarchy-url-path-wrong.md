---
title: "Patch MDVA-32634: spostamento errato della categoria nella gerarchia url_path"
description: La patch MDVA-32634 risolve il problema per cui l'url\_path della categoria di catalogo non cambia dopo lo spostamento della categoria nella gerarchia. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.3.
exl-id: a445dea6-3834-479b-9044-b6d2b863a0b5
feature: Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 0%

---

# Patch MDVA-32634: spostamento errato della categoria nella gerarchia url_path

La patch MDVA-32634 risolve il problema per cui l&#39;url\_path della categoria di catalogo non cambia dopo lo spostamento della categoria nella gerarchia. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.4-p2

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud e Adobe Commerce on-premise 2.3.1 - 2.4.1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Lo spostamento di una categoria di catalogo nella gerarchia causa un url\_path errato. URL\_path della categoria assegnata all&#39;ambito di archiviazione predefinito \[ **id:0** \] rimane invariata dopo lo spostamento della categoria nella gerarchia.

<u>Passaggi da riprodurre</u>:

1. Accedi all’amministratore di Commerce. Crea la seguente struttura di categorie sotto la categoria radice: move-cat sub-move-cat sub-move-cat2 new-cat-move
1. Verificare l&#39;attributo categoria \[ url\_path \] \[ id: 120 \] per l&#39;assegnazione dei valori nella tabella \[ catalog\_category\_entity\_varchar \] utilizzando la query seguente:

   ```sql
   SELECT * FROM catalog_category_entity_varchar WHERE attribute_id = 120 ORDER BY value_id DESC LIMIT 4;
   ```

   Dovrebbe fornire il seguente risultato:

   ```sql
   MariaDB [m24dev]> SELECT * FROM catalog_category_entity_varchar WHERE attribute_id = 120 ORDER BY value_id DESC LIMIT 4;
   ```

   \[ url\_path \] valori generati e assegnati all&#39;ambito Tutti gli archivi \[ 0 \]. Questo è corretto rispetto a un’istanza senza B2B.
1. Vai all’elenco delle categorie back-end, trascina \[ move-cat \] e rilascialo in \[ new-cat-move \]. Ora la categoria dovrebbe assomigliare a: nuovo-gatto-mossa-gatto-mossa-gatto-mossa-gatto-gatto2
1. Controllare la tabella \[ catalog\_category\_entity\_varchar \] utilizzando la query seguente:

   ```sql
   SELECT * FROM catalog_category_entity_varchar WHERE attribute_id = 120 ORDER BY value_id DESC LIMIT 16;
   ```

<u>Risultati previsti</u>:

Anche l&#39;URL\_path assegnato a tutto l&#39;ambito dell&#39;archivio \[ 0 \] deve essere aggiornato con il nuovo percorso.

<u>Risultati effettivi</u>:

L&#39;URL\_path assegnato a tutto l&#39;ambito di archiviazione \[ 0 \] rimane invariato, anche se dopo lo spostamento non è disponibile alcun percorso di questo tipo. Inoltre, sono stati creati nuovi valori url\_path per ciascun archivio.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
