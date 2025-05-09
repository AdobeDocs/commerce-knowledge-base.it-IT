---
title: '"MDVA-43824: azione di annullamento dell''ordine non riuscita. Errore: "L''elemento non è stato annullato""'
description: "La patch MDVA-43824 risolve il problema relativo all'errore di annullamento dell'ordine: *L'elemento non è stato annullato*. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13. L'ID della patch è MDVA-43824. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.5."
exl-id: e4d839d6-84ed-4157-80a1-fd482fef897c
feature: Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# MDVA-43824: azione di annullamento dell&#39;ordine non riuscita. Errore: &quot;L&#39;elemento non è stato annullato&quot;

La patch di MDVA-43824 risolve il problema relativo all&#39;annullamento dell&#39;ordine non riuscito. Errore: *L&#39;elemento non è stato annullato*. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13. L&#39;ID della patch è MDVA-43824. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.6 - 2.3.7-p3, 2.4.1 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;ordine effettuato da un cliente connesso non può essere annullato. L&#39;azione di annullamento dell&#39;ordine non è riuscita a causa del seguente errore:

```
Zend_Db_Statement_Exception: SQLSTATE[23000]: Integrity constraint violation: 1452 Cannot add or update a child row: a foreign key constraint fails (`mer33515_ee24developpbdevelop`.`salesrule_customer`, CONSTRAINT `SALESRULE_CUSTOMER_RULE_ID_SEQUENCE_SALESRULE_SEQUENCE_VALUE` FOREIGN KEY (`rule_id`) REFERENCES `sequence_salesrule` (`sequen), query was: INSERT INTO `salesrule_customer` () VALUES (){code}
```

<u>Passaggi da riprodurre</u>:

1. Crea una regola di vendita (il tipo di coupon è &quot;Coupon specifico&quot; o &quot;No Coupon&quot;).
1. Vai alla vetrina, accedi come cliente e aggiungi un prodotto al carrello.
1. Vai al carrello e applica la regola del prezzo del carrello se la regola del prezzo del carrello ha un coupon come &quot;Coupon specifico&quot;. La regola del prezzo del carrello deve essere applicata correttamente.
1. Vai a pagamento e inserire l&#39;ordine con qualsiasi metodo di pagamento.
1. Vai a Amministrazione Commerce > **Vendite** > **Ordini**.
1. Apri l’ordine effettuato nel passaggio 4.
1. Fare clic sul pulsante **Annulla**.

<u>Risultati previsti</u>:

L&#39;ordine è stato annullato senza alcun errore.

<u>Risultati effettivi</u>:

Azione di annullamento dell&#39;ordine non riuscita con il seguente errore: *L&#39;elemento non è stato annullato.*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella documentazione per gli sviluppatori.
