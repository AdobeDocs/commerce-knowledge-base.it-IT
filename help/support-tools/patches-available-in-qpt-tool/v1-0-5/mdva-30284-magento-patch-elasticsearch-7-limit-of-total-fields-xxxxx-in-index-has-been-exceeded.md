---
title: "Patch MDVA-30284: Elasticsearch 7 - È stato superato il limite dei campi totali [XXXXX] nell'indice"
description: La patch MDVA-30284 risolve il problema relativo al superamento del "Limite dei campi totali \[XXXXX\] nell'indice" quando si utilizza l'Elasticsearch 7. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.5. L'ID della patch è MDVA-30284.
exl-id: cf840558-891a-4a7e-8900-b8434f703be0
feature: Search, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# Patch MDVA-30284: Elasticsearch 7 - È stato superato il limite dei campi totali [XXXXX] nell&#39;indice

La patch MDVA-30284 risolve il problema relativo al superamento del &quot;Limite dei campi totali \[XXXXX\] nell&#39;indice&quot; quando si utilizza l&#39;Elasticsearch 7. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.5. L&#39;ID della patch è MDVA-30284.

## Prodotti e versioni interessati

* La patch è stata progettata per Adobe Commerce su infrastruttura cloud 2.3.5-p2
* L’Elasticsearch 7 è compatibile con Adobe Commerce 2.3.5 e 2.4.x

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il limite dei campi di Elasticsearch non è corretto e causa il seguente errore durante l’esecuzione dell’indicizzatore \[catalogsearch\_fulltext\]:

*Il limite dei campi totali [xxx] nell&#39;indice [xxxxxx] è stato superato*

Questo problema si verifica quando si dispone di un numero elevato di attributi di prodotto. Il problema viene attivato dal modo in cui Elasticsearch calcola il conteggio dei campi. Talvolta, quando sono presenti attributi a cui sono assegnati campi, questi campi vengono indicizzati come indicizzatori separati. Questo comporta un superamento del limite di avvertenza.

<u>Passaggi da riprodurre:</u>

<u>Prerequisiti</u>

* Modulo installato-elasticsearch 100.3.5.
* Elasticsearch 7 installato.
* Imposta l’Elasticsearch come backend di ricerca.

1. Crea più di 1000 attributi per i prodotti.
1. Crea prodotti per ogni famiglia.
1. Esegui indicizzatore.

<u>Risultato previsto:</u>

Tutti i prodotti sono disponibili nell’indice Elasticsearch.

<u>Risultato effettivo:</u>

1. Errore di Elasticsearch:

   ```
    {"error":{"root_cause":[{"type":"illegal_argument_exception","reason":"Limit
    of total fields [3000] in index [magento2_product_2_v11] has been exceeded"}],"type":"illegal_argument_exception","reason":"Limit
    of total fields [3000] in index [magento2_product_2_v11] has been exceeded"},"status":400}
   ```

1. Nuovo prodotto non indicizzato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
