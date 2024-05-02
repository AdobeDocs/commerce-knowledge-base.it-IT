---
title: "ACSD-50336: e-mail di avviso sul prodotto non inviate"
description: Applica la patch ACSD-50336 per risolvere il problema di Adobe Commerce, in cui le e-mail di avviso sul prodotto non vengono inviate quando un prodotto è di nuovo disponibile o il prezzo viene modificato.
exl-id: 0fc51603-e74d-4ce7-9e67-42826ffbfab2
feature: Communications, Personalization, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-50336: e-mail di avviso sul prodotto non inviate

La patch ACSD-50336 risolve il problema che impedisce l&#39;invio delle e-mail di avviso sui prodotti quando un prodotto è di nuovo disponibile o quando il prezzo viene modificato. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30. L’ID della patch è ACSD-50336. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p1 - 2.4.4-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le e-mail di avviso sul prodotto non vengono inviate quando un prodotto è di nuovo in magazzino o il prezzo viene modificato.

<u>Prerequisiti</u>:

Imposta avvisi sui prodotti per quando un prodotto viene reinserito nell&#39;archivio.

<u>Passaggi da riprodurre</u>:

1. Accedi come cliente sulla vetrina.
1. Apri un prodotto non disponibile.
1. Iscriviti per ricevere una notifica quando il prodotto è *torna a magazzino*.
1. Aggiorna il prodotto da [!UICONTROL Admin] essere _torna a magazzino_.

<u>Risultati previsti</u>:

Una notifica e-mail relativa al prodotto *torna a magazzino* viene inviato al cliente.

<u>Risultati effettivi</u>:

Il cliente non riceve una notifica e-mail relativa al prodotto *torna a magazzino*. Nel registro viene visualizzato il seguente errore:

```
report. CRITICAL: Magento\ProductAlert\Model\Mailing\ErrorEmailSender::execute(): Argument #2 ($storeId) must be of type int, string given, called in vendor/magento/module-product-alert/Model/Mailing/AlertProcessor.php on line 130 [] [] 
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
