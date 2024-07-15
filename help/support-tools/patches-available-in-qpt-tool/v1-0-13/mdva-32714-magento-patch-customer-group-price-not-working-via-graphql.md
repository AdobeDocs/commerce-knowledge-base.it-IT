---
title: "Patch MDVA-32714: il prezzo del gruppo di clienti non funziona tramite GraphQL"
description: La patch MDVA-32714 risolve il problema in cui сil prezzo del gruppo del cliente non viene aggiunto nella risposta alla query del prodotto GraphQL. Questa patch è disponibile quando è installato QPT 1.0.13 (Quality Patches Tool). Il problema è pianificato per essere risolto in Adobe Commerce 2.4.3.
exl-id: a4fc92ad-68dc-437d-8577-303007ef8a92
feature: GraphQL, Customer Service, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# Patch MDVA-32714: il prezzo del gruppo di clienti non funziona tramite GraphQL

>[!WARNING]
>
>Una nuova patch denominata MDVA-33975 risolve i problemi di calcolo dei prezzi di GraphQL. MDVA-32714 è obsoleto e si consiglia di applicare la patch MDVA-33975. Per accedere a questa patch, fare riferimento alla [patch MDVA-33975: calcoli dei prezzi GraphQL](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/mdva-33975-magento-patch-graphql-price-calculations.html) nella Knowledge Base del supporto tecnico.

La patch MDVA-32714 risolve il problema in cui сil prezzo del gruppo del cliente non viene aggiunto nella risposta alla query del prodotto GraphQL. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.4.0

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud e Adobe Commerce on-premise 2.3.4 - 2.4.0-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il prezzo di gruppo del cliente per il cliente generico non viene aggiunto nella risposta alla query del prodotto GraphQL.

<u>Passaggi da riprodurre</u>:

1. Abilitare e impostare il prezzo speciale per qualsiasi prodotto per qualsiasi gruppo di clienti.
1. Utilizza la query prodotto in GraphQL per richiamare i prezzi per questo prodotto, come descritto in: [Query prodotti > Query di esempio](https://devdocs.magento.com/guides/v2.4/graphql/queries/products.html#sample-queries) nella documentazione per gli sviluppatori.

<u>Risultati previsti</u>:

```api
price_range
```

visualizza il prezzo scontato per i clienti generali in base a quanto definito nel pannello di amministrazione.

<u>Risultati effettivi</u>:

```api
price_range
```

non visualizza il prezzo scontato per i clienti generici.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta le [patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
