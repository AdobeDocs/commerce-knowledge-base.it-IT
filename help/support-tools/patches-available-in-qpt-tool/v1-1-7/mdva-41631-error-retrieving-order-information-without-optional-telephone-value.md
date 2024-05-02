---
title: '''MDVA-41631: errore durante il recupero delle informazioni sull''ordine senza valore "phone" opzionale'''
description: La patch MDVA-41631 risolve il problema che causa un errore nel recupero delle informazioni sull'ordine senza il valore "phone" opzionale tramite GraphQL. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
exl-id: 94b0b918-c1f9-4f5d-8fcd-8b92a9ca8c59
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-41631: errore durante il recupero delle informazioni sull&#39;ordine senza il valore &quot;phone&quot; opzionale

La patch MDVA-41631 risolve il problema che causa un errore nel recupero delle informazioni sull&#39;ordine senza il valore &quot;phone&quot; opzionale tramite GraphQL. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli utenti ricevono un errore durante il recupero delle informazioni dell’ordine senza il valore &quot;phone&quot; opzionale tramite GraphQL.

<u>Passaggi da riprodurre</u>:

1. Vai a **Archivia** > **Configurazione** > **Clienti** > **Configurazione cliente** > **Opzioni nome e indirizzo** > **Mostra telefono** e impostare il numero di telefono come facoltativo.
1. Effettua un ordine utilizzando l’API di GraphQL come cliente connesso.
   * Non impostare il numero di telefono quando si impostano gli indirizzi di fatturazione e spedizione. Seguire le istruzioni fornite in [Tutorial su GraphQL Checkout](https://devdocs.magento.com/guides/v2.4/graphql/tutorials/checkout/checkout-customer.html) nella documentazione per gli sviluppatori.
1. Recuperare l’ordine utilizzando GraphQL [query customerOrders](https://devdocs.magento.com/guides/v2.4/graphql/queries/customer-orders.html).

<pre>
<code class="language-graphql">
{
  customer {
    firstname
    lastname
    suffix
    email

    orders(filter:{number:{eq:"000000001"}}){
        items{
          billing_address {
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
}
shipping_address {
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
}
        }
    }
  }
}
</code>
</pre>

<u>Risultati previsti</u>:

Gli utenti ricevono informazioni sull’ordine.

<u>Risultati effettivi</u>:

Gli utenti ricevono il seguente errore: *&quot;message&quot;: &quot;Internal server error&quot;,*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
