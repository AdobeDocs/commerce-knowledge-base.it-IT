---
title: "ACSD-46988: la richiesta API della valuta GraphQL restituisce valori Null"
description: La patch ACSD-46988 risolve il problema per cui la richiesta API della valuta GraphQL restituisce valori Null per una valuta personalizzata. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21. L’ID della patch è ACSD-46988. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.
exl-id: 8da0ab99-8db9-4222-9400-6df1520267f0
feature: REST, GraphQL
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-46988: la richiesta API della valuta GraphQL restituisce valori null

La patch ACSD-46988 risolve il problema per cui la richiesta API della valuta GraphQL restituisce valori Null per una valuta personalizzata. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21. L’ID della patch è ACSD-46988. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La richiesta API per la valuta GraphQL restituisce valori Null per una valuta personalizzata.

<u>Passaggi da riprodurre</u>:

1. Configurare la valuta personalizzata in Admin. Vai a **Sistema** > **Configurazione** > **Generale** > **Impostazione valuta**.
1. Invia una richiesta GraphQL con il seguente payload:

<pre>
<code class="language-graphql">
{
    currency {
        base_currency_code
        base_currency_symbol
        default_display_currency_code
        default_display_currency_symbol
        available_currency_codes
        exchange_rates {
            currency_to
            rate
        }
    }
}
</code>
</pre>

<u>Risultati previsti</u>:

La richiesta restituisce valori di valuta invece di valori nulli.

<u>Risultati effettivi</u>:

La richiesta restituisce più valori Null.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Strumenti patch di qualità > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida allo strumento Patch di qualità.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Passaggi aggiuntivi necessari dopo l&#39;installazione della patch

Per gli utenti locali:

* Esegui: `composer require symfony/intl:"~5.4.11"`

Per gli utenti di Cloud:

* Esegui: `composer require symfony/intl:"~5.4.11"`
* Push `composer.json` e `composer.lock` nell’archivio git insieme al file patch.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida allo strumento Patch di qualità.
