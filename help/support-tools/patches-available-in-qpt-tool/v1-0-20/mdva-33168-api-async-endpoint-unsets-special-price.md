---
title: "MDVA-33168: l’endpoint API asincrono annulla il prezzo speciale"
description: La patch MDVA-33168 risolve il problema per cui l'utilizzo dell'endpoint asincrono API per aggiornare un attributo di prodotto annulla l'impostazione di un prezzo speciale.
exl-id: 4dd26215-b140-4924-8f4d-0d062e5fda2d
feature: REST, Orders, Personalization
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---

# MDVA-33168: l&#39;endpoint asincrono API annulla il prezzo speciale

La patch MDVA-33168 risolve il problema per cui l&#39;utilizzo dell&#39;endpoint asincrono API per aggiornare un attributo di prodotto annulla l&#39;impostazione di un prezzo speciale.

Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20. L&#39;ID della patch è MDVA-33168. Il problema è pianificato per la risoluzione in Adobe Commerce versione 2.4.3.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.3-p1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud e Adobe Commerce on-premise 2.3.3 - 2.4.2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Passaggi da riprodurre</u>:

1. Crea due siti Web con negozi.
1. Vai a **Negozi > Configurazioni > Catalogo > Catalogo > Prezzo > Catalogo** e imposta **Limite prezzo** = *Sito Web*.
1. Creare un *text-type* attributo del prodotto. Lascia tutte le opzioni predefinite.
1. Aggiungi l&#39;attributo creato al set di attributi predefinito.
1. Crea un prodotto semplice da utilizzare con un prodotto bundle.
1. Crea un prodotto bundle con le seguenti opzioni di esempio:
   * **Abilita prodotto** = *Sì*.
   * **Set di attributi** = *Predefinito*.
   * **Nome prodotto** = *bundle-1*.
   * **SKU** = *bundle-1*.
   * **SKU dinamica** = *Sì*.
   * **Prezzo** = *100,00 $*.
   * **Classe imposta** = *Merci tassabili*.
   * **Stato Stock** = *In magazzino*.
1. Sotto **Elementi bundle**, imposta le seguenti opzioni di esempio:
   * **Articoli del bundle di spedizione** = *Insieme*.
   * **Titolo opzione** = *test*, **Tipo di input** = *Pulsanti di scelta*, **Obbligatorio** checkbox = *selezionato*.
   * **È predefinito** checkbox = *non selezionato*.
   * **Nome** = *simple-100*.
   * **SKU** = *simple-100*.
   * **Prezzo** = *100,00*.
   * **Tipo di prezzo** = *Fisso*.
   * **Quantità predefinita** = *1*.
   * **Definito dall&#39;utente** checkbox = *non selezionato*.
1. Passare all&#39;ambito del negozio non predefinito e impostare il prezzo speciale. (Esempio: su **Advanced Pricing** pagina, imposta **Prezzo speciale** = *4%*, e **Visualizzazione prezzo** = *Fascia di prezzo*.)
1. Aggiorna il nuovo attributo solo nell&#39;ambito dell&#39;archivio non predefinito, come nell&#39;esempio seguente:

   ```php
       PUT {{base_url}}/rest/en_au/async/V1/products/{{sku}}    {        "product": {            "custom_attributes": [                {                    "attribute_code": "text_attr",                    "value": 21                                   }            ]                    }    }
   ```

<u>Risultati previsti</u>:

Altri valori di attributo rimangono invariati quando si aggiorna un attributo di prodotto utilizzando l’API REST asincrona, come previsto.

<u>Risultati effettivi</u>:

Il prezzo speciale, impostato utilizzando l’API rest asincrona nell’ambito dello store, viene rimosso.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
