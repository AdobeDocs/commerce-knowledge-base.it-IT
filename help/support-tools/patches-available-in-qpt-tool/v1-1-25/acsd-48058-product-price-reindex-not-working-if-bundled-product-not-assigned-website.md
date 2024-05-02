---
title: "ACSD-48058: la reindicizzazione del prezzo del prodotto non funziona se il prodotto in bundle non è stato assegnato al sito web"
description: Applica la patch ACSD-48058 per risolvere il problema di Adobe Commerce in cui la reindicizzazione del prezzo del prodotto non funziona se il prodotto incluso non è assegnato ad alcun sito Web.
exl-id: 691371f1-7f10-4be6-80e4-821e7cf664a6
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-48058: la reindicizzazione del prezzo del prodotto non funziona se il prodotto in bundle non è stato assegnato al sito web

La patch ACSD-48058 risolve il problema che causa il mancato funzionamento della reindicizzazione del prezzo del prodotto se il prodotto incluso non è assegnato ad alcun sito Web. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25. L’ID della patch è ACSD-48058. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) >=2.4.5 &lt; 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La reindicizzazione dei prezzi del prodotto non funziona se il prodotto nel pacchetto non è assegnato ad alcun sito Web.

<u>Passaggi da riprodurre</u>:

1. Vai a Amministrazione di Adobe Commerce > **[!UICONTROL Catalog]** > **[!UICONTROL Products]** e creare un nuovo prodotto o modificare un prodotto già incluso.
   * Fai clic sul pulsante **[!UICONTROL Product in Websites]** e deselezionare tutte le caselle di controllo (siti Web)
   * Salvare il prodotto
1. Eseguire la reindicizzazione.

<u>Risultati previsti</u>:

Reindicizzazione eseguita correttamente.

<u>Risultati effettivi</u>:

Durante l’esecuzione dell’indice dei prezzi del prodotto viene generato il seguente errore:

```bash
Undefined array key <bundel product id > in vendor/magento/module-bundle/Model/ResourceModel/Indexer/Price/DisabledProductOptionPriceModifier.php on line 117
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
