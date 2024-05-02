---
title: "MDVA-40601: impossibile recuperare i dati sulla categoria modificata dall'aggiornamento pianificato tramite GraphQL"
description: La patch di qualità di MDVA-40601 Adobe Commerce risolve il problema relativo all'errore restituito dagli utenti quando ottengono informazioni sulla categoria modificata tramite l'aggiornamento pianificato tramite GraphQL. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.3. L'ID della patch è MDVA-40601. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
exl-id: b1ea93e7-8d4a-4bdd-8267-cc60de25bd39
feature: Categories, GraphQL
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# MDVA-40601: impossibile recuperare i dati sulla categoria modificata dall&#39;aggiornamento pianificato tramite GraphQL

La patch di qualità di MDVA-40601 Adobe Commerce risolve il problema relativo all&#39;errore restituito dagli utenti quando ottengono informazioni sulla categoria modificata tramite l&#39;aggiornamento pianificato tramite GraphQL. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.3. L&#39;ID della patch è MDVA-40601. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.3 e 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.1 - 2.4.2-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli utenti ricevono un errore durante il tentativo di recuperare informazioni sulla categoria modificata dall’aggiornamento pianificato tramite GraphQL.

<u>Passaggi da riprodurre</u>:

1. Imposta una struttura di categorie con una sottocategoria come indicato di seguito:

   <pre>
   <code class="language-graphql">
   - Root
    - Some category
         - Some child category
   </code>
   </pre>

1. Esegui la query GraphQL con ID &quot;Some Category&quot; 49.

   <pre>
    <code class="language-graphql">
    query {
     category(id: 49) {
      name
      children {
        name
       }
     }
   }
   </code>
   </pre>

   Risultato:

   <pre>
    <code class="language-graphql">
    {
      "data": {
        "category": {
          "name": "Some category",
          "children": [
            {
              "name": "Some child category"
            }
          ]
        }
      }
    }
    </code>
    </pre>

1. Crea un aggiornamento della pianificazione per &quot;Alcune categorie&quot; con un nome di categoria diverso.
1. Attendi l’attivazione dell’aggiornamento della pianificazione.
1. Esegui la stessa query indicata in precedenza.

<u>Risultati previsti</u>:

Si riceve lo stesso risultato ma con il nome della categoria aggiornato.

<u>Risultati effettivi</u>:

Viene visualizzato il seguente errore:

<pre>
<code class="language-graphql">
{
  "errors": [
    {
      "debugMessage": "uasort() expects parameter 1 to be array, string given",
      "message": "Internal server error",
      "extensions": {
        "category": "internal"
      },
      "locations": [
        {
          "line": 2,
          "column": 3
        }
      ],
      "path": [
        "category"
      ]
    }
  ],
  "data": {
    "category": null
  }
}
</code>
</pre>

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti a seconda del tipo di distribuzione:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sulle patch di qualità per Adobe Commerce, consulta:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sezione.
