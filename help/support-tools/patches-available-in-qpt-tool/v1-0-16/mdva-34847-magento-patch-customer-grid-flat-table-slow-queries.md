---
title: "MDVA-34847: query lente della tabella customer_grid_flat"
description: La patch MDVA-34847 risolve il problema relativo alla presenza di query lente nella tabella "customer_grid_flat". Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16. Il problema è stato risolto nella versione 2.4.3 di Adobe Commerce.
exl-id: e91cb86d-83cd-4267-a132-64465a57da7f
feature: Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# MDVA-34847: query lente della tabella customer_grid_flat

La patch MDVA-34847 risolve il problema relativo alla lentezza delle query nella tabella `customer_grid_flat`. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16. Il problema è stato risolto nella versione 2.4.3 di Adobe Commerce.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.3

**Compatibile con le versioni Adobe:**

Adobe Commerce sull’infrastruttura cloud e Adobe Commerce on-premise 2.3.0 - 2.4.2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Nella tabella `customer_grid_flat` si verificano query lente.

<u>Passaggi da riprodurre</u>:

1. Crea un utente amministratore con ambito personalizzato (esempio: Imposta **GWS** = *0,* e scegli il sito Web predefinito esistente con **ID** = *1*).
1. Crea qualsiasi elemento di prodotto e categoria.
1. Effettua un ordine dal front-end.
1. Accedi all’amministratore come nuovo utente.
1. Vai alla griglia vendite (**Vendite > Ordini**).
1. Verificare che la query SQL sia stata inviata al database.

<u>Risultati previsti</u>:

L’estensione GWS per l’amministrazione deve utilizzare

```sql
int
```

valori di

```sql
website_id
```

in condizioni SQL, come previsto, ad esempio:

```sql
main_table.website_id IN (1)
```

<u>Risultati effettivi</u>:

L’estensione Admin GWS ha aggiunto una condizione con

```sql
website_id
```

valore come

```sql
string
```

, come:

```sql
main_table.website_id IN ('1')
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
