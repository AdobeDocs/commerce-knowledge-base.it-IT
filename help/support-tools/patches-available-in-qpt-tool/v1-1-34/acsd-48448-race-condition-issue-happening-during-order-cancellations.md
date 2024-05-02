---
title: "ACSD-48448: problema di condizione di gara durante l’annullamento dell’ordine che causa la duplicazione dell’immissione nella tabella inventory_booking"
description: Applica la patch ACSD-48448 per risolvere il problema di prestazioni di Adobe Commerce in cui si verifica il problema di condizione Race durante gli annullamenti dell’ordine, che causa la duplicazione delle voci nella tabella inventory_booking.
feature: Orders, Checkout
role: Admin
exl-id: 69d00219-bc9f-4531-9e85-38476c2258ed
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-48448 *[!UICONTROL Race]* problema di condizione durante l’annullamento dell’ordine che causa la duplicazione dell’immissione `inventory_reservation` tabella

La patch ACSD-48448 risolve il problema in cui *[!UICONTROL Race]* si verifica un problema di condizione durante l’annullamento dell’ordine, che causa la duplicazione delle voci nel `inventory_reservation` tabella. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.34. L’ID della patch è ACSD-48448. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p2 e 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.6-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

*[!UICONTROL Race]* si verifica un problema di condizione durante l’annullamento dell’ordine, che causa la duplicazione delle voci nel `inventory_reservation` tabella.

<u>Passaggi da riprodurre</u>:

1. Effettua un ordine.
1. Controlla la `inventory_reservation` tabella per verificare che sia presente un record per `order_placed` evento.
1. Esegui lo script allegato per annullare l’ordine in parallelo (ricorda di modificare l’URL e orderID).

`bash cancel_order.sh`

```
#!/bin/bash
baseUrl=" "
orderId=3
token=$(curl --location --request POST "${baseUrl}rest/V1/integration/admin/token" \
 -H 'Content-Type: application/json' \
 -d '{
  "username": "admin",
  "password": "password"
}')
echo ${token//\"/}
curl --location --request POST "${baseUrl}/rest/V1/orders/${orderId}/cancel" \
 -H "Authorization:Bearer ${token//\"/}" \
 -H 'Content-Type: application/json' \
 &
sleep 0.1;
curl --location --request POST "${baseUrl}/rest/V1/orders/${orderId}/cancel" \
 -H "Authorization:Bearer ${token//\"/}" \
 -H 'Content-Type: application/json' \
wait
```

<u>Risultati previsti</u>:

I record non vengono duplicati.

<u>Risultati effettivi</u>:

I record duplicati vengono creati nel `inventory_reservation` tabella per `order_canceled`.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
