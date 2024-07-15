---
title: '''MDVA-34886: nessun risultato di ricerca quando si utilizza l''attributo "weight"'
description: La patch MDVA-34886 risolve il problema per cui la ricerca restituisce risultati quando l'attributo weight è configurato come ricercabile. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16. Il problema è stato risolto nella versione 2.4.3 di Adobe Commerce.
exl-id: e6f33772-0167-4a54-9d62-0ab89edb5d1d
feature: Attributes, Cache, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# MDVA-34886: nessun risultato di ricerca quando si utilizza l’attributo &quot;weight&quot;

La patch MDVA-34886 risolve il problema per cui la ricerca restituisce risultati quando l&#39;attributo weight è configurato come ricercabile. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16. Il problema è stato risolto nella versione 2.4.3 di Adobe Commerce.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.5-p1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud e Adobe Commerce on-premise 2.3.2 - 2.4.2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La ricerca restituisce risultati quando l’attributo weight è configurato come ricercabile.

<u>Passaggi da riprodurre</u>:

1. Configura Elasticsearch.
1. Passa a **Amministratore** > **Archivi** > **Attributi** > **Prodotto**. Modificare l&#39;attributo **Weight** e impostarne l&#39;attributo **Searchable** = *Yes*.
1. Salva l’attributo e cancella la cache di configurazione.
1. Nel front-end, cercare un valore di testo (esempio: *bag*).
1. La ricerca non restituisce alcun risultato.
1. Il registro eccezioni conterrà un messaggio di errore simile al seguente:

```php
{"type":"number_format_exception","reason":"For input string: \"bag\""}
```

<u>Risultati previsti</u>:

La ricerca restituisce risultati anche quando l’attributo weight è configurato come ricercabile, come previsto.

<u>Risultati effettivi</u>:

La ricerca non restituisce risultati quando l’attributo weight è configurato come ricercabile.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
