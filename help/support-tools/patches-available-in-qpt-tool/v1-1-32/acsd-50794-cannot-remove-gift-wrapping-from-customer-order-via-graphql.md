---
title: 'ACSD-50794: impossibile rimuovere la confezione regalo dall''ordine del cliente tramite GraphQL'
description: Applica la patch ACSD-50794 per risolvere il problema di Adobe Commerce che impedisce agli utenti di rimuovere la confezione regalo dall’ordine del cliente tramite GraphQL.
exl-id: 4983910c-9ea0-451e-a2b6-81485184bbce
feature: Gift, GraphQL, Orders
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-50794: impossibile rimuovere la confezione regalo dall&#39;ordine del cliente tramite GraphQL

La patch ACSD-50794 risolve il problema che impediva agli utenti di rimuovere la confezione regalo dall’ordine del cliente tramite GraphQL. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.32. L’ID della patch è ACSD-50794. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli utenti non possono rimuovere la confezione regalo dall’ordine del cliente tramite GraphQL.

<u>Passaggi da riprodurre</u>:

1. Crea un cliente dal front-end.
1. Crea un prodotto semplice.
1. Abilita *[!UICONTROL Gift Messages]* andando in **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Gift Options]** e impostando *[!UICONTROL Allow Gift Messages]* = *[!UICONTROL Yes]*.
1. Crea *[!UICONTROL Gift Wrapping]* andando in **[!UICONTROL Stores]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Gift Wrapping]**.
1. Ottieni token cliente.
1. Crea un carrello vuoto, customerCart.
   * Aggiungi prodotti al carrello: `addProductsToCart` mutazione
   * Imposta indirizzo di fatturazione: `setBillingAddressOnCart` mutazione
   * Imposta indirizzo di spedizione: `setShippingAddressesOnCart` mutazione
   * Imposta metodo di spedizione: mutazione `setShippingMethodsOnCart` (velocità piatta)
   * Imposta metodo di pagamento: mutazione `setPaymentMethodOnCart` (checkmo)
1. Ora controlla la confezione regalo *Uid* con questa query del carrello:

   <pre><code class="language-GraphQL">
    &lbrace;
      cart(cart_id: "{{CART_ID}}") &lbrace;
        available_gift_wrappings&lbrace;
            uid
        &rbrace;
    &rbrace;
    &rbrace;
    </code></pre>

1. Impostare il wrapping regalo utilizzando `setGiftOptionsOnCart`.
1. Controlla la query cart: cart.
1. Annullare l&#39;impostazione del wrapping regalo utilizzando `setGiftOptionsOnCart` (valore impostato su null).
1. Di nuovo, controlla la query cart: cart.
1. Ordine dei luoghi: mutazione `placeOrder`.
1. Esegui query cliente: cliente.

   <pre><code class="language-graphql">
    query &lbrace;
      customer &lbrace;
        firstname
        middlename
        lastname
        suffix
        email
        orders &lbrace;
            items &lbrace;
                order_date
                gift_wrapping &lbrace;
                    design
                    uid
                &rbrace;
            &rbrace;
        &rbrace;
        addresses &lbrace;
          firstname
          middlename
          lastname
          street
          city
          region &lbrace;
            region_code
            region
          &rbrace;
          postcode
          country_code
          telephone
        &rbrace;
      &rbrace;
    &rbrace;
    </code></pre>

<u>Risultati previsti</u>:

Una volta che un utente imposta un gift wrap e lo annulla, la query del cliente restituisce null.

<u>Risultati effettivi</u>:

La query del cliente restituisce comunque la confezione regalo come applicata.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
