---
title: '"ACSD-57074: l’attributo personalizzato *Yes/No* con il prefisso "price_*" nell’attributo "attribute_code" non funziona con l’indicizzazione"'
description: Applica la patch ACSD-57074 per risolvere il problema di Adobe Commerce per cui l’attributo personalizzato *Yes/No* con prefisso "price_*" nell’attributo "attribute_code" non funziona con l’indicizzazione.
feature: Products, Categories, Catalog Management
role: Admin, Developer
exl-id: c620722f-a66d-4cae-9614-becec589a78c
source-git-commit: 4197f2a8f3d4775d3459b17bd92fa51a54ff9607
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-57074 *Sì/No* attributo personalizzato con `price_*` prefisso in `attribute_code` l&#39;attributo non funziona con l&#39;indicizzazione

La patch ACSD-57074 risolve il problema in cui *Sì/No* attributo personalizzato con `price_*` prefisso in `attribute_code` L&#39;attributo non funziona con l&#39;indicizzazione. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.47. L’ID della patch è ACSD-57074. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il *Sì/No* attributo personalizzato con `price_*` prefisso in `attribute_code` L&#39;attributo non funziona con l&#39;indicizzazione.

<u>Passaggi da riprodurre</u>:

1. Crea un attributo di prodotto personalizzato con le seguenti opzioni:
   * *[!UICONTROL Catalog Input Type]*: *Sì/No*
   * *[!UICONTROL Scope]*: *StoreView*
   * *[!UICONTROL Use in Search]*: *Sì*
1. Assegnare l&#39;attributo al set di attributi predefinito.
1. Crea un prodotto con l’attributo creato.
1. Assegna il prodotto appena creato a una categoria.
1. Esegui reindicizzazione completa.

<u>Risultati previsti</u>:

Il prodotto viene visualizzato nella categoria assegnata.

<u>Risultati effettivi</u>:

Il prodotto non viene visualizzato nella pagina iniziale della categoria.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
