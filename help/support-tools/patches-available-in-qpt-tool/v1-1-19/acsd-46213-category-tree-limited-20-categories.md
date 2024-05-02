---
title: "ACSD-46213: richiesta di struttura ad albero della categoria limitata a 20 categorie"
description: '"La patch ACSD-46213 risolve il problema se la richiesta della struttura delle categorie è limitata a 20 categorie. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.19. L’ID della patch è ACSD-46213. '''
exl-id: 27a18871-8552-4ecd-9e03-0dc38d037ea0
feature: Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# ACSD-46213: richiesta di struttura della categoria limitata a 20 categorie

La patch ACSD-46213 risolve il problema se la richiesta della struttura delle categorie è limitata a 20 categorie. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.19. L’ID della patch è ACSD-46213.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.


## Problema

La richiesta dell’albero delle categorie è limitata a 20 categorie.

<u>Passaggi da riprodurre</u>:

1. Crea una categoria sotto la categoria principale.
1. Crea 24 sottocategorie nella categoria principale creata nel passaggio 1.
1. Esegui la seguente richiesta GraphQL:

   <pre>
    <code class="language-graphql">
    {
      categoryList(filters: { parent_id: { in: ["3"] } }) {
        name
        level
        path
        url_path
        children {
          id
          level
          name
          path
          url_path
          url_key
          children {
            uid
            level
            name
            path
            url_path
            url_key
          }
        }
      }
    }
    </code>
    </pre>

1. Controlla i risultati.

<u>Risultati previsti</u>:

Mostra 24 categorie.

<u>Risultati effettivi</u>:

Mostra solo 20 categorie.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
