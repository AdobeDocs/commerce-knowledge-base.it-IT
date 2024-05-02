---
title: "MDVA-42806: a ogni aggiornamento della società viene inviata una nuova e-mail di registrazione società"
description: La patch MDVA-42806 risolve il problema dell'invio di un'e-mail di registrazione a una nuova società ogni volta che una società esistente viene aggiornata tramite l'API REST. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9. L'ID della patch è MDVA-42806. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: 957b89f7-cd4d-4c94-8d1d-c30442aafa6a
feature: REST, B2B, Communications, Companies
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# MDVA-42806: ogni volta che si aggiorna una società, viene inviata una nuova e-mail di registrazione della società

La patch MDVA-42806 risolve il problema dell&#39;invio di un&#39;e-mail di registrazione a una nuova società ogni volta che una società esistente viene aggiornata tramite l&#39;API REST. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9. L&#39;ID della patch è MDVA-42806. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Ogni volta che una società esistente viene aggiornata tramite API REST, viene inviata una nuova e-mail di registrazione della società.

<u>Prerequisiti</u>:

Moduli B2B installati.

<u>Passaggi da riprodurre</u>:

1. Crea un account aziendale.
1. Utilizzare `/V1&#x200B;/company&#x200B;/<company_id>` endpoint. Per aggiornare la società creata, consulta [aggiorna la società](https://devdocs.magento.com/guides/v2.4/b2b/company-object.html#update-the-company) nella documentazione per gli sviluppatori. Di seguito è riportato un payload di esempio:

```php
{
    "company": {
        "id": 2,
        "status": 1,
        "company_name": "Company",
        "company_email": "company@example.test",
        "street": [
            "Test"
        ],
        "city": "Test",
        "country_id": "US",
        "region_id": "1",
        "postcode": "12345",
        "telephone": "8009994301",
        "customer_group_id": 2,
        "sales_representative_id": 1,
        "super_user_id": 2
    }
}
```

<u>Risultati previsti</u>:

Non viene inviata alcuna e-mail che indichi &quot;Nuova richiesta di registrazione società&quot; poiché l’API sta aggiornando una società esistente.

<u>Risultati effettivi</u>:

Ad ogni invio della richiesta API viene inviata un’e-mail con la dicitura &quot;Nuova richiesta di registrazione dell’azienda&quot;.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
