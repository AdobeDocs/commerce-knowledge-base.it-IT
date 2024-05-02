---
title: "MDVA-28300: problema di calcolo del prezzo con la regola del prezzo di catalogo in GraphQL"
description: La patch di MDVA-28300 risolve il problema che impedisce alla richiesta di GraphQL di riflettere le modifiche di prezzo dalle regole di prezzo del catalogo. Questa patch è disponibile quando è installato QPT (Quality Patches Tool) v.1.0.6. Il problema è stato risolto nella versione 2.3.6 di Adobe Commerce.
exl-id: 86079d29-db69-4758-a159-aeed8e0ea21f
feature: Catalog Management, GraphQL, Customer Service, Marketing Tools, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 0%

---

# MDVA-28300: problema di calcolo del prezzo con la regola del prezzo di catalogo in GraphQL

>[!WARNING]
>
>Una nuova patch denominata MDVA-33975 risolve i problemi di calcolo dei prezzi di GraphQL. MDVA-28300 è obsoleto e si consiglia di applicare la patch MDVA-33975. Per accedere a questa patch, fare riferimento a [MDVA-33975: calcolo dei prezzi GraphQL](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/mdva-33975-magento-patch-graphql-price-calculations.html).

La patch di MDVA-28300 risolve il problema che impedisce alla richiesta di GraphQL di riflettere le modifiche di prezzo dalle regole di prezzo del catalogo. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6. Il problema è stato risolto nella versione 2.3.6 di Adobe Commerce.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:** Adobe Commerce on-premise 2.3.5-p1

**Compatibile con le versioni di Adobe Commerce:** Adobe Commerce on-premise e Adobe Commerce on cloud infrastructure 2.3.0 - 2.3.5-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando una regola del prezzo di catalogo viene applicata a un determinato gruppo di clienti, i prezzi degli articoli nel carrello e il totale dell’ordine non vengono calcolati correttamente in GraphQL.

<u>Passaggi da riprodurre:</u>

1. Crea un nuovo account cliente e cambia il gruppo di clienti in Commercio all’ingrosso.
1. Creare una nuova regola di catalogo in **Marketing** > **Promozioni** > **Regole prezzo catalogo** con i seguenti parametri:
   * Gruppi di clienti: Azioni all’ingrosso:
   * Applica: *Applica come percentuale dell&#39;originale*
   * Sconto: *50*


1. Crea un nuovo prodotto con prezzo=100.
1. Accedi al front-end utilizzando l’account cliente creato in precedenza (se hai già effettuato l’accesso, esci e accedi di nuovo).
1. Aggiungi il prodotto al carrello. Il prezzo del prodotto è 50 (prezzo regolare 100) e totale ordine: 55 (50 + 5 del costo di spedizione).
1. Eseguire la chiamata API GraphQL descritta in [query customerCart](https://devdocs.magento.com/guides/v2.3/graphql/queries/customer-cart.html) nella documentazione per gli sviluppatori.

<u>Risultato previsto:</u>

Sia API che frontend hanno lo stesso totale ordine con lo sconto introdotto dalla regola di catalogo applicata.

<u>Risultato effettivo:</u>

Il totale dell&#39;ordine non applica lo sconto della regola del catalogo.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Applicare le patch utilizzando lo strumento Patch di qualità](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html).

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento alla sezione Patch disponibili in QPT.
