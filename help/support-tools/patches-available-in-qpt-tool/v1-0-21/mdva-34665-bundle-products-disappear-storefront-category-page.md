---
title: "MDVA-34665: i prodotti bundle scompaiono dalla pagina delle categorie della vetrina"
description: La patch MDVA-34665 risolve il problema relativo ai prodotti in bundle mancanti nelle pagine delle categorie. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21. L'ID della patch è MDVA-34665. Il problema è stato risolto nella versione 2.4.3 di Adobe Commerce.
exl-id: 2b393f91-de0d-4c54-89db-5e2af13f93a6
feature: Categories, Products, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 0%

---

# MDVA-34665: i prodotti bundle scompaiono dalla pagina delle categorie della vetrina

La patch MDVA-34665 risolve il problema relativo ai prodotti in bundle mancanti nelle pagine delle categorie. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21. L&#39;ID della patch è MDVA-34665. Il problema è stato risolto nella versione 2.4.3 di Adobe Commerce.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.4-p2

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce on-premise e Adobe Commerce sull’infrastruttura cloud 2.3.4-2.3.4-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

**Caso 1:**

<u>Prerequisiti</u>:

1. Crea 15.000 prodotti in bundle con un solo prodotto semplice come opzione bundle. Non utilizzare lo stesso prodotto semplice con più prodotti in bundle.
1. I prodotti semplici devono essere impostati su *Non visibili singolarmente*.

<u>Passaggi da riprodurre</u>:

1. Assegna 15.000 prodotti in bundle in due categorie, 7.500 ciascuna.
1. Selezionare tutti i prodotti semplici (15k) e aggiornare il materiale utilizzando gli aggiornamenti degli attributi di massa del prodotto. Il nostro obiettivo è disporre di molti ID nella tabella delle licenze di ricerca (le tabelle delle licenze sono le tabelle utilizzate dall’indicizzatore per individuare i record da aggiornare).
1. Verificare di disporre di 15.000 ID nella tabella `catalogsearch_fulltext_cl`.
1. Verificare che l&#39;indicizzatore `indexer_update_all_views` sia eseguito.
1. Eseguire una query continua sulla pagina della categoria e osservare il conteggio dei prodotti.

<u>Risultati previsti</u>:

Il conteggio dei prodotti deve rimanere invariato dopo la reindicizzazione.

<u>Risultati effettivi</u>:

Il numero di prodotti scende a 7.450 dopo un po&#39;. Rimane in 7.450 anche al termine dell’indicizzazione.

**Caso 2:**

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto bundle con un prodotto semplice associato come opzione.
1. Modifica le modalità dell&#39;indicizzatore in *aggiorna secondo la pianificazione*.
1. Assegna il prodotto bundle a una categoria.
1. Cambia lo stato delle scorte del prodotto semplice in *esaurito*.
1. Esegui cron; il prodotto bundle scompare dalla vetrina.
1. Aggiungete nuovamente le scorte al prodotto semplice e salvatele.
1. Esegui l&#39;indicizzatore cron.
1. Aggiorna la pagina della categoria.

<u>Risultati previsti</u>:

Prodotto ancora assente.

<u>Risultati effettivi</u>:

Viene visualizzato di nuovo il bundle prodotto.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
