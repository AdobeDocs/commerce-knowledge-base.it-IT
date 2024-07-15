---
title: "MDVA-30599: customer_is_guest non è impostato correttamente"
description: La patch MDVA-30599 risolve il problema relativo alle virgolette dei guest create utilizzando l'API e contrassegnate in modo errato come virgolette per i clienti connessi. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6. Il problema è stato risolto in Adobe Commerce 2.4.2.
exl-id: e16bb926-241b-451e-89a5-33000f73c5b7
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# MDVA-30599: customer_is_guest non è impostato correttamente

La patch MDVA-30599 risolve il problema relativo alle virgolette dei guest create utilizzando l&#39;API e contrassegnate in modo errato come virgolette per i clienti connessi. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6. Il problema è stato risolto in Adobe Commerce 2.4.2.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.5-p2

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.4 - 2.4.0

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le virgolette degli ospiti create utilizzando l’API non vengono contrassegnate correttamente come virgolette per i clienti connessi.

<u>Passaggi da riprodurre</u>:

1. Nella vetrina di Adobe Commerce, aggiungi un prodotto al carrello come utente ospite.
1. Nel tuo Adobe Commerce DB, trova il `quote_id_mask` corrispondente.
1. Invia una richiesta API all&#39;interfaccia archivio carrello `quoteGuestCartRepositoryV1` per i carrelli guest. Può essere eseguito tramite Swagger o richiesta cURL.

```curl
curl -X GET "http://web2-73.sparta.corp.magento.com/dev/support/ee24dev/rest/all/V1/guest-carts/ToOwPtSBxkorkCLq6ztwupPd99y8zhky" -H "accept: application/json"
```

<u>Risultati previsti</u>:

In risposta si ottiene `"customer_is_guest": true`

<u>Risultati effettivi</u>:

In risposta si ottiene `"customer_is_guest": false`

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Passaggi aggiuntivi necessari dopo l&#39;installazione della patch

La patch sarà efficace per tutti i nuovi carrelli ospiti. Se è necessario correggere i carrelli guest esistenti, impostare `quote.customer_is_guest = 1` per i record in cui `quote.customer_id` è NULL. Puoi eseguire una query simile alla seguente:

```sql
UPDATE quote SET customer_is_guest = 1 WHERE customer_id IS NULL;
```

>[!WARNING]
>
>Si consiglia vivamente di testare la query nell’ambiente di staging/integrazione prima di eseguirla in produzione. Consigliamo inoltre di avere un backup recente prima di qualsiasi manipolazione con DB.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
