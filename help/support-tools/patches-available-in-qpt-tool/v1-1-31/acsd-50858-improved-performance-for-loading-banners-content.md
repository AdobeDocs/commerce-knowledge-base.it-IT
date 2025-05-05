---
title: "ACSD-50858: prestazioni migliorate per il caricamento del contenuto dei banner"
description: Applica la patch ACSD-50858 per risolvere il problema di Adobe Commerce, in cui le prestazioni del banner sono influenzate nella pagina carrello/pagamento a causa di query eccessive sul database e di un aumento del tempo di caricamento della pagina.
exl-id: f9526d66-fc0e-44a0-8c72-b9f183004840
feature: Page Content
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# ACSD-50858: prestazioni migliorate per il caricamento del contenuto dei banner

La patch ACSD-50858 risolve un problema di prestazioni del banner nella pagina carrello/pagamento: *query database eccessive e aumento del tempo di caricamento della pagina*. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.31. L’ID della patch è ACSD-50858. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le prestazioni del banner sono influenzate nella pagina carrello/pagamento a causa di *query sul database eccessive e aumento del tempo di caricamento delle pagine*.

Questo problema è stato risolto refactoring del modo in cui vengono caricati i contenuti dei banner, che ha ridotto il numero di query DB del 99,99% e il tempo di caricamento della pagina di circa il 99%.

<u>Passaggi da riprodurre</u>:

1. Accedi ad Admin e crea un prodotto semplice.
1. Crea un cliente, dall’amministratore o dal front-end, e aggiungi un indirizzo di spedizione.
1. Spostare banners.php nella cartella `magento_root/pub/`.
1. Generare i banner utilizzando il comando `php pub/banners.php`. Verranno generati 10.000 banner semplici e 1.000 banner con regole di vendita.
1. Accedi al cliente creato in precedenza sul front-end.
1. Aggiungi al carrello il prodotto creato in precedenza.
1. Vai alla pagina di pagamento (pagamento/carrello).
1. Monitorare il tempo di caricamento della richiesta `banner/ajax/load`:

   * Senza `bin/magento dev:query-log:enable`
   * Con `bin/magento dev:query-log:enable`

     ```
     grep 'magento_banner_content' var/debug/db.log  | wc -l
     ```

<u>Risultati previsti</u>:

Diminuzione del numero di query DB per `magento_banner_content` e del tempo di caricamento del carrello/pagina di pagamento.

<u>Risultati effettivi</u>:

Aumento del numero di query DB per `magento_banner_content` e del tempo di caricamento del carrello/pagina di pagamento.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Informazioni aggiuntive

<u>contenuto banners.php</u>:

```php
\Banner::class);
    $banner->setIsEnabled(
        \Magento\Banner\Model\Banner::STATUS_ENABLED
    )->setName(
        'Test Dynamic Block '.$i
    )->setTypes(
        ''
    )->setStoreContents(
        [0 => 'Dynamic Block Content '.$i]
    )->save();
}

$objectManager = \Magento\Framework\App\ObjectManager::getInstance();

/** @var \Magento\SalesRule\Model\Rule $salesRule */
$salesRule = $objectManager->create(\Magento\SalesRule\Model\Rule::class);
$salesRule->setData(
    [
        'name' => '50% Off ',
        'is_active' => 1,
        'customer_group_ids' => [\Magento\Customer\Model\GroupManagement::NOT_LOGGED_IN_ID],
        'coupon_type' => \Magento\SalesRule\Model\Rule::COUPON_TYPE_NO_COUPON,
        'conditions' => [
            [
                'type' => \Magento\SalesRule\Model\Rule\Condition\Address::class,
                'attribute' => 'base_subtotal',
                'operator' => '>',
                'value' => 0
            ]
        ],
        'simple_action' => 'by_percent',
        'discount_amount' => 50,
        'discount_step' => 0,
        'stop_rules_processing' => 1,
        'website_ids' => [
           1
        ]
    ]
);
$salesRule->save();

for ($i = 0; $i < 1000; $i++) {

    $banner = $objectManager->create(\Magento\Banner\Model\Banner::class);
    $banner->setData(
        [
            'name' => 'Get 50% Off ',
            'is_enabled' => \Magento\Banner\Model\Banner::STATUS_ENABLED,
            'types' => [], /*Any Banner Type*/
            'store_contents' => ['<img src="http://example.com/banner_40_percent_off.png" />'],
            'banner_sales_rules' => [$salesRule->getId()],
        ]
    );
    $banner->save();
}
```

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
