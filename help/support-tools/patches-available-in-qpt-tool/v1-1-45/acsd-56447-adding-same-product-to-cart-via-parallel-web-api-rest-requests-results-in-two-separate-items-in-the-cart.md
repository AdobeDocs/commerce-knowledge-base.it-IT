---
title: 'ACSD-56447: l’aggiunta dello stesso prodotto al carrello tramite API REST web parallelo determina due elementi separati nel carrello'
description: Applica la patch ACSD-56447 per risolvere il problema di Adobe Commerce, in cui l’aggiunta dello stesso prodotto al carrello tramite richieste API REST web parallele genera due elementi separati nel carrello.
feature: Shopping Cart, REST
role: Admin, Developer
exl-id: c63874be-a8a6-4143-adaa-ba3e9e107dd4
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# ACSD-56447: l’aggiunta dello stesso prodotto al carrello tramite API REST web parallelo determina due elementi separati nel carrello

La patch ACSD-56447 risolve il problema per cui l’aggiunta dello stesso prodotto al carrello tramite richieste API REST web parallele genera due elementi separati nel carrello. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45. L’ID della patch è ACSD-56447. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’aggiunta dello stesso prodotto al carrello tramite richieste API REST web parallele determina due elementi separati nel carrello.

<u>Passaggi da riprodurre</u>:

1. Genera un token cliente per effettuare la richiesta di chiamate REST API utilizzando [!DNL Postman].
1. Crea un carrello per il cliente.
1. Utilizza il token generato in precedenza per creare un carrello vuoto per il cliente.
1. Utilizzare CURL per eseguire due richieste `AddProductsToCart` in parallelo. Segui le istruzioni riportate nell&#39;[Esercitazione sull&#39;elaborazione dell&#39;ordine](https://developer.adobe.com/commerce/webapi/rest/tutorials/orders/) nella documentazione per gli sviluppatori.

<u>Risultati previsti</u>:

Gli articoli con più quantità vengono visualizzati in una riga.

<u>Risultati effettivi</u>:

Gli stessi SKU vengono visualizzati in più righe.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
