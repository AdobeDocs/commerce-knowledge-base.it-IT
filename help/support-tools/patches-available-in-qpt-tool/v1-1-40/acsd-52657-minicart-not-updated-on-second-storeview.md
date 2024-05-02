---
title: "ACSD-52657: Minicart non aggiornato nel secondo storeview che utilizza il sottodominio"
description: Applica la patch ACSD-52657 per risolvere il problema Adobe Commerce, se il minicart non viene aggiornato nella seconda visualizzazione store che utilizza un sottodominio.
feature: Shopping Cart
role: Admin, Developer
exl-id: d0877a15-800e-4e10-9ace-ebb7f26dbd18
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-52657: Minicart non aggiornato nel secondo storeview che utilizza il sottodominio

La patch ACSD-52657 risolve il problema se il minicart non viene aggiornato nella seconda visualizzazione store che utilizza un sottodominio. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40. L’ID della patch è ACSD-52657. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Minicart non viene aggiornato nella visualizzazione archivio secondaria che utilizza un sottodominio.

<u>Passaggi da riprodurre</u>:

1. Crea un secondo storeview e configura un sottodominio per l’URL di base.
1. Aggiorna il dominio dei cookie in modo che abbia il dominio comune.
1. Nel negozio principale, aggiungi un prodotto al carrello.
1. Aggiorna la seconda visualizzazione dello store, quindi vai alla pagina del carrello.

<u>Risultati previsti</u>:

Il carrello e il minicart vengono aggiornati nel sottodominio.

<u>Risultati effettivi</u>:

Il miniart non viene aggiornato quando il negozio secondario viene aggiornato, ma la pagina del carrello mostra il prodotto aggiunto e puoi effettuare un ordine in quella sessione (`PHPSESSID` cookie è condiviso).

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
