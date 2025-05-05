---
title: 'MDVA-40601: impossibile recuperare i dati sulla categoria modificata dall''aggiornamento pianificato tramite GraphQL'
description: La patch di qualità di MDVA-40601 Adobe Commerce risolve il problema relativo all'errore restituito dagli utenti quando ottengono informazioni sulla categoria modificata tramite l'aggiornamento pianificato tramite GraphQL. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.3. L'ID della patch è MDVA-40601. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
exl-id: b1ea93e7-8d4a-4bdd-8267-cc60de25bd39
feature: Categories, GraphQL
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# MDVA-40601: impossibile recuperare i dati sulla categoria modificata dall&#39;aggiornamento pianificato tramite GraphQL

La patch di qualità di MDVA-40601 Adobe Commerce risolve il problema relativo all&#39;errore restituito dagli utenti quando ottengono informazioni sulla categoria modificata tramite l&#39;aggiornamento pianificato tramite GraphQL. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.3. L&#39;ID della patch è MDVA-40601. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.3 e 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.1 - 2.4.2-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

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
    query &lbrace;
     category(id: 49) &lbrace;
      name
      children &lbrace;
        name
       &rbrace;
     &rbrace;
   &rbrace;
   </code>
   </pre>

   Risultato:

   <pre>
    <code class="language-graphql">
    &lbrace;
      "data": &lbrace;
        "category": &lbrace;
          "name": "Some category",
          "children": &lbrack;
            &lbrace;
              "name": "Some child category"
            &rbrace;
          &rbrack;
        &rbrace;
      &rbrace;
    &rbrace;
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
&lbrace;
  "errors": &lbrack;
    &lbrace;
      "debugMessage": "uasort() expects parameter 1 to be array, string given",
      "message": "Internal server error",
      "extensions": &lbrace;
        "category": "internal"
      &rbrace;,
      "locations": &lbrack;
        &lbrace;
          "line": 2,
          "column": 3
        &rbrace;
      &rbrack;,
      "path": &lbrack;
        "category"
      &rbrack;
    &rbrace;
  &rbrack;,
  "data": &lbrace;
    "category": null
  &rbrace;
&rbrace;
</code>
</pre>

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti a seconda del tipo di distribuzione:

&#x200B;* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
&#x200B;* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sulle patch di qualità per Adobe Commerce, consulta:

&#x200B;* [È stato rilasciato lo strumento Quality Patches: è stato introdotto un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
&#x200B;* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
