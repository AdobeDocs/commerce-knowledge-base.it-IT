---
title: 'MDVA-43601: i trigger vengono rimossi dalla tabella "catalogrule_product_price" dopo la reindicizzazione completa'
description: La patch MDVA-43601 risolve il problema in cui i trigger vengono rimossi dalla tabella "catalogrule_product_price" dopo una reindicizzazione completa di "catalogrule_rule" o "catalogrule_product". Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13. L'ID della patch è MDVA-43601. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: fdef1e56-79ec-455a-8a29-b82f1c8ceea7
feature: Catalog Management, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# MDVA-43601: i trigger vengono rimossi dalla tabella &quot;catalogrule_product_price&quot; dopo la reindicizzazione completa

La patch di MDVA-43601 risolve il problema relativo alla rimozione dei trigger dalla tabella `catalogrule_product_price` dopo una reindicizzazione completa di `catalogrule_rule` o `catalogrule_product`. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13. L&#39;ID della patch è MDVA-43601. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I trigger vengono rimossi dalla tabella `catalogrule_product_price` dopo una reindicizzazione completa di `catalogrule_rule` o `catalogrule_product`.

<u>Passaggi da riprodurre</u>:

1. Imposta tutti gli indicizzatori su *Aggiorna secondo pianificazione*.
1. Controllare i trigger creati per la tabella `catalogrule_product_price` eseguendo la seguente richiesta SQL:

   ```sql
   show triggers like '%catalogrule_%'\G
   ```

1. Reindicizzare manualmente `catalogrule_rule` o `catalogrule_product` eseguendo il comando seguente: `bin/magento indexer:reindex catalogrule_rule`
1. Controllare nuovamente i trigger della tabella `catalogrule_product_price`.

<u>Risultati previsti</u>:

I trigger nella tabella `catalogrule_product_price` vengono mantenuti dopo una reindicizzazione completa.

<u>Risultati effettivi</u>:

Nessun trigger trovato per la tabella `catalogrule_product_price`.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella documentazione per gli sviluppatori.
