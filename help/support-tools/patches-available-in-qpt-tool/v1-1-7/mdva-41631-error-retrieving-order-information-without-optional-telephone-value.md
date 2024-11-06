---
title: '''MDVA-41631: errore durante il recupero delle informazioni sull''ordine senza valore "phone" opzionale'''
description: La patch MDVA-41631 risolve il problema che causa un errore nel recupero delle informazioni sull'ordine senza il valore "phone" opzionale tramite GraphQL. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
exl-id: 94b0b918-c1f9-4f5d-8fcd-8b92a9ca8c59
feature: Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-41631: errore durante il recupero delle informazioni sull&#39;ordine senza il valore &quot;phone&quot; opzionale

La patch MDVA-41631 risolve il problema che causa un errore nel recupero delle informazioni sull&#39;ordine senza il valore &quot;phone&quot; opzionale tramite GraphQL. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli utenti ricevono un errore durante il recupero delle informazioni dell’ordine senza il valore &quot;phone&quot; opzionale tramite GraphQL.

<u>Passaggi da riprodurre</u>:

1. Vai a **Store** > **Configurazione** > **Clienti** > **Configurazione cliente** > **Opzioni nome e indirizzo** > **Mostra telefono** e imposta il numero di telefono come facoltativo.
1. Effettua un ordine utilizzando l’API di GraphQL come cliente connesso.
   * Non impostare il numero di telefono quando si impostano gli indirizzi di fatturazione e spedizione. Segui le istruzioni fornite nell&#39;[Esercitazione estrazione GraphQL](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/checkout-customer.html) nella documentazione per sviluppatori.
1. Recupera l&#39;ordine utilizzando la query [customerOrders](https://developer.adobe.com/commerce/webapi/graphql/queries/customer-orders.html) di GraphQL.

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

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella documentazione per gli sviluppatori.
