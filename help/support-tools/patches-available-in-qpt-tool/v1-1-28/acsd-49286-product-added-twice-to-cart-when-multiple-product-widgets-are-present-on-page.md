---
title: "ACSD-49286: prodotto aggiunto due volte al carrello quando sono presenti più widget di prodotto"
description: Applica la patch ACSD-49286 per risolvere il problema di Adobe Commerce, in cui il prodotto viene aggiunto due volte al carrello quando sulla pagina sono presenti più widget di prodotto.
exl-id: b1764943-945d-4ef9-9bbe-3f3c8383b5b1
feature: Admin Workspace, Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-49286: prodotto aggiunto due volte al carrello quando sono presenti più widget di prodotto

La patch ACSD-49286 risolve il problema se il prodotto viene aggiunto due volte al carrello quando sulla pagina sono presenti più widget di prodotto. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28. L’ID della patch è ACSD-49286. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il prodotto viene aggiunto due volte al carrello quando sulla pagina sono presenti più widget di prodotto.

<u>Passaggi da riprodurre</u>:

1. Accedi ad Admin e vai su **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Page]** > **[!UICONTROL Home Page]**
1. Nella sezione dei contenuti, fai clic su **[!UICONTROL Edit]** utilizzo [!DNL Page Builder].
1. Aggiungi due elementi riga a **[!UICONTROL Content]**.
1. Aggiungi prodotti in entrambi gli elementi riga.
1. Nella prima riga, imposta l&#39;aspetto del prodotto come [!UICONTROL Product Grid] e selezionare una categoria da visualizzare.
1. Nella seconda riga, imposta l&#39;aspetto del prodotto come [!UICONTROL Product Carousel] e selezionare un&#39;altra categoria da visualizzare.
1. Vai alla vetrina **[!UICONTROL Home Page]** e aggiungi un prodotto dalla griglia prodotti.
1. Aggiungi un altro prodotto da [!UICONTROL Product Carousel].

<u>Risultati previsti</u>:

La quantità di prodotto non deve raddoppiare dopo l’aggiunta di un prodotto al carrello da [!UICONTROL Product Grid].

<u>Risultati effettivi</u>:

La quantità di prodotto raddoppia dopo l’aggiunta di un prodotto al carrello da [!UICONTROL Product Grid].

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud. 

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
