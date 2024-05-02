---
title: "MDVA-20376: entità con customerId non esistente"
description: La patch MDVA-20376 risolve il problema di un errore *No such entity with customerId = 1* per i clienti connessi dopo il posizionamento dell'ordine. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13. Il problema è stato risolto nella versione 2.3.4 di Adobe Commerce.
exl-id: a12865d0-4ac2-444f-b8b6-22cae249f5d4
feature: Variables
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# MDVA-20376: entità con customerId non esistente

La patch MDVA-20376 risolve il problema di un *Nessuna entità di questo tipo con customerId = 1* errore per i clienti connessi dopo il posizionamento dell’ordine. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13. Il problema è stato risolto nella versione 2.3.4 di Adobe Commerce.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.2

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.2 - 2.3.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I clienti connessi ricevono *Nessuna entità di questo tipo con customerId = 1* errore dopo il posizionamento dell’ordine.

<u>Passaggi da riprodurre</u>:

1. Passa alla vetrina e accedi come utente registrato.
1. Effettua un ordine.
1. Nella CLI, vai a `var/log` e vedrai il `exception.log` file.

<u>Risultati previsti</u>:

Non dovrebbero comparire errori nei registri, come previsto.

<u>Risultati effettivi</u>:

Il registro eccezioni viene compilato con errori simili ai seguenti:

```php
report.CRITICAL: No such entity with customerId = 1 {"exception":"[object] (Magento\\Framework\\Exception\\NoSuchEntityException(code: 0): No such entity with customerId = 1 at /mnt/data/home/nyarlaga/dev/232/vendor/magento/framework/Exception/NoSuchEntityException.php:50)"} []
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
