---
title: "ACSD-48784: prezzi dei segmenti dei clienti memorizzati nella cache non correttamente tra i gruppi di clienti"
description: Applica la patch ACSD-48784 per risolvere il problema di Adobe Commerce, in cui i prezzi dei segmenti dei clienti non vengono memorizzati correttamente nella cache tra i gruppi di clienti.
exl-id: 6be11fd0-5c93-4ac7-8664-7e2a289c9e38
feature: Admin Workspace, Cache, Customer Service, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-48784: i prezzi del segmento cliente non sono memorizzati correttamente nella cache tra i gruppi di clienti

La patch ACSD-48784 risolve il problema in cui i prezzi dei segmenti dei clienti vengono memorizzati nella cache in modo errato tra i gruppi di clienti. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28. L’ID della patch è ACSD-48784. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I prezzi del segmento cliente non vengono memorizzati nella cache correttamente tra i gruppi di clienti.

<u>Prerequisiti</u>:

Configurare [!DNL Varnish] o [!DNL Fastly].

<u>Passaggi da riprodurre</u>:

1. Abilita il caching di pagine intere nello store.
1. Accedi al sito come utente con prezzi speciali per gruppi di clienti.
1. Vai a una pagina di prodotto per un prodotto con prezzi speciali per gruppi di clienti. Osserva il *prezzo speciale*.
1. In un browser separato, apri la stessa pagina di prodotto di un utente guest senza effettuare l’accesso. Osserva il prezzo regolare.
1. Accedere all&#39;interfaccia di amministrazione di Adobe Commerce e cancellare la cache di Adobe Commerce e [!DNL Fastly] per questo archivio.
1. Nel browser connesso, rimuovere il cookie `X-Magento-Vary`.
1. Nel browser connesso, ricarica più volte la stessa pagina di prodotto fino a quando il caching non è completamente scaricato.
1. Nel browser non connesso, ricarica la pagina del prodotto per visualizzare ora i prezzi del gruppo di clienti.

<u>Risultati previsti</u>:

La pagina del prodotto mostra il prezzo corretto per specifici gruppi di clienti.

<u>Risultati effettivi</u>:

* Gli utenti ospiti visualizzano il prezzo speciale dell&#39;utente connesso.
* Il mini carrello mostra il prezzo corretto una volta che il prodotto è aggiunto ad esso.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
