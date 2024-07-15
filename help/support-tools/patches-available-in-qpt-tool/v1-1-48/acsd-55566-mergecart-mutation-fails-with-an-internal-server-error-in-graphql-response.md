---
title: "ACSD-55566: la mutazione [!UICONTROL mergeCart] non riesce e viene restituito un errore interno del server in [!DNL GraphQL] risposta"
description: Applica la patch ACSD-55566 per risolvere il problema di Adobe Commerce in cui la mutazione "mergeCart" non riesce e genera un errore interno del server nella risposta  [!DNL GraphQL]  durante l'unione dei carrelli di origine e di destinazione che hanno gli stessi elementi del bundle.
feature: GraphQL, Shopping Cart
role: Admin, Developer
exl-id: 84a9b861-351e-4fcc-bb91-3e31c7ae24e6
source-git-commit: 6b8eecb3df0bb32344a5861a604a40402bb4d392
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-55566: la mutazione `mergeCart` non riesce con errore interno del server nella risposta [!DNL GraphQL]

La patch ACSD-55566 risolve il problema se la mutazione `mergeCart` non riesce e nella risposta [!DNL GraphQL] viene restituito un errore interno del server. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48. L’ID della patch è ACSD-55566. Il problema è pianificato per essere risolto in Adobe Commerce 2.5.0.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.6-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La mutazione `mergeCart` non riesce e nella risposta [!DNL GraphQL] si verifica un errore interno del server quando si uniscono i carrelli di origine e di destinazione con gli stessi elementi bundle.

<u>Passaggi da riprodurre</u>:

1. Crea un’origine personalizzata e un titolo personalizzato.
1. Assegna il titolo creato al sito Web principale.
1. Creare un prodotto semplice e assegnargli l’origine creata (qty=2).
1. Crea un prodotto bundle con un’opzione e un prodotto secondario (prodotto creato al passaggio 3).
1. Crea un carrello guest tramite [!DNL GraphQL].
1. Aggiungi un prodotto bundle con entrambe le opzioni selezionate.
1. Salva *cartID*.
1. Crea un cliente e genera un token cliente.
1. Crea un carrello clienti.
1. Aggiungi al carrello lo stesso prodotto bundle con la stessa configurazione.
1. Prova a unire il carrello ospiti con il carrello clienti.

<u>Risultati previsti</u>:

Il carrello clienti contiene i prodotti di entrambi i carrelli.

<u>Risultati effettivi</u>:

Viene visualizzato un errore interno.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
