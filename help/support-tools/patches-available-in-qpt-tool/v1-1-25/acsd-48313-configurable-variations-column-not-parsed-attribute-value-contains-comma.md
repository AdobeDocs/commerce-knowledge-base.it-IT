---
title: '"ACSD-48313: [!UICONTROL configurable_variations] colonna non analizzata se il valore dell’attributo contiene la virgola'
description: Applicare la patch ACSD-48313 per risolvere il problema Adobe Commerce in cui [!UICONTROL configurable_variations] La colonna non viene analizzata se il valore dell’attributo contiene una virgola.
exl-id: 0ac3f8da-4da3-4308-bea4-98a5b6926b0d
feature: Attributes, Configuration
role: Admin
source-git-commit: 4cb43c4f16238253fc7fc75d9af9b921dfa74158
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# ACSD-48313 **[!UICONTROL configurable_variations]** colonna non analizzata se il valore dell’attributo contiene una virgola

La patch ACSD-48313 risolve il problema dove **[!UICONTROL configurable_variations]** La colonna non viene analizzata se il valore dell’attributo contiene una virgola. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25. L’ID della patch è ACSD-48313. La versione in cui verrà risolto il problema non è ancora disponibile.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.4-p5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Dopo l’esportazione di prodotti configurabili, il file risultante non può essere importato nuovamente a causa di un problema di formattazione con **[!UICONTROL configurable_variations]** attributo. Ciò si verifica quando sono presenti opzioni di attributo che includono una virgola.

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** e crea un nuovo attributo _Dimensione_:
1. Tipo di input catalogo per il proprietario del negozio: **[!UICONTROL Dropdown]**.
1. Crea opzioni che includono una virgola, ad esempio:
   * 10,2 cm
   * 15,5 cm
1. **[!UICONTROL Advanced Attribute Properties]** - Portata: _Globale_.
1. Crea un nuovo prodotto configurabile utilizzando la funzionalità Crea configurazioni.
1. Seleziona l’attributo precedente _Dimensione_ e le due opzioni che includono la virgola.
1. Vai a **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]** e crea una nuova esportazione di prodotti (esegui la cron per attivare la generazione del file CSV).
1. Vai a **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]** e prova a reimportare lo stesso file CSV creato in precedenza.

<u>Risultati previsti</u>:

L’utente deve essere in grado di importare il file.

<u>Risultati effettivi</u>:

```
1. Column configurable_variations: Attribute with code "2cm" does not exist or is missing from product attribute set in row(s): 3
2. Column configurable_variations: Attribute with code "5cm" does not exist or is missing from product attribute set in row(s): 3
3. Column configurable_variations: Invalid option value for attribute "size" in row(s): 3
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
