---
title: "Patch MDVA-33516: errore di modifica elenco richieste di acquisto prodotto in bundle"
description: La patch di MDVA-33516 risolve il problema che si verifica quando si modifica il tipo di prodotto del bundle dall'Elenco richieste di acquisto, quando si viene reindirizzati a una pagina di errore dell'elemento dell'elenco richieste di acquisto. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.14. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.3.
exl-id: 76a16982-f977-4674-b05e-23f4ac355d52
feature: B2B, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# Patch MDVA-33516: errore Modifica elenco richieste di acquisto prodotto in bundle

La patch di MDVA-33516 risolve il problema che si verifica quando si modifica il tipo di prodotto del bundle dall&#39;Elenco richieste di acquisto, quando si viene reindirizzati a una pagina di errore dell&#39;elemento dell&#39;elenco richieste di acquisto. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.14. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.4

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.0 - 2.3.5-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Errore durante la modifica dei prodotti inclusi nell&#39;elenco richieste di acquisto.

<u>Prerequisiti</u>:

* B2B è installato.
* Elenco richieste di acquisto abilitato.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto in bundle con due prodotti semplici.
1. Vai alla pagina del prodotto nel pacchetto, fai clic sul pulsante **Personalizza e aggiungi al carrello**.
1. Selezionare una delle opzioni dal menu a discesa, fare clic su **Aggiungi all&#39;elenco richieste** per creare un nuovo elenco richieste. Per i passaggi dettagliati, fare riferimento alla [Guida utente di Magento > Elenchi richieste di acquisto personali > Creazione di un elenco richieste di acquisto](https://docs.magento.com/user-guide/customers/account-dashboard-requisition-lists.html#create-a-requisition-list) nella guida utente.
1. Passare all&#39;elenco di richieste di acquisto appena creato (Conto personale > **Elenchi di richieste di acquisto personali**).
1. Fare clic sul pulsante **Visualizza** nella colonna *Azioni*.
1. Fai clic sul pulsante **Modifica**.

<u>Risultati previsti</u>:<br>

Nessun errore.

<u>Risultati effettivi</u>:

Pagina &quot;Personalizzazione&quot;, contenente un’immagine del prodotto in bundle, il prezzo e il seguente messaggio di errore:

```
Fatal error: Uncaught Error: Call to a member function isAvailableForCompare() on null in /var/www/html/var/view_preprocessed/pub/static/vendor/magento/module-catalog/view/frontend/templates/product/view/addto/compare.phtml:1 Stack trace: #0 /var/www/html/vendor/magento/framework/View/TemplateEngine/Php.php(59): include() #1 /var/www/html/vendor/magento/framework/View/Element/Template.php(271): Magento\Framework\View\TemplateEngine\Php->render(Object(Magento\Catalog\Block\Product\View\AddTo\Compare), '/var/www/html/v...', Array) #2 /var/www/html/vendor/magento/framework/View/Element/Template.php(301): Magento\Framework\View\Element\Template->fetchView('/var/www/html/v...') #3 /var/www/html/vendor/magento/framework/View/Element/AbstractBlock.php(1099): Magento\Framework\View\Element\Template->_toHtml() #4 /var/www/html/vendor/magento/framework/View/Element/AbstractBlock.php(1103): Magento\Framework\View\Element\AbstractBlock->Magento\Framework\View\Element   {closure} () #5 /var/www/html/vendor/magento/framework/View/Element/ in /var/www/html/var/view_preprocessed/pub/static/vendor/magento/module-catalog/view/frontend/templates/product/view/addto/compare.phtml
  on line 1
```

## Applicare la patch

Per applicare singole patch, utilizzare i seguenti collegamenti, a seconda del prodotto Adobe Commerce:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili nello strumento QPT, fare riferimento alla sezione [Patch disponibili nello strumento QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
