---
title: "MDVA-40401: il valore di utilizzo del coupon cambia dopo un ordine non riuscito"
description: La patch MDVA-40401 risolve il problema relativo alla modifica del valore di utilizzo dei coupon anche dopo un ordine non riuscito. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4. L'ID della patch è MDVA-40401. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
exl-id: c497ee84-9c20-4c75-ad3a-3b71f699acbf
feature: Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# MDVA-40401: il valore di utilizzo del coupon cambia dopo un ordine non riuscito

La patch MDVA-40401 risolve il problema relativo alla modifica del valore di utilizzo dei coupon anche dopo un ordine non riuscito. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4. L&#39;ID della patch è MDVA-40401. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p2

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli utenti non possono riapplicare il coupon dopo averlo utilizzato in un ordine non riuscito.

<u>Passaggi da riprodurre</u>:

1. Crea una regola del carrello con i coupon generati automaticamente.
1. Aggiungi un prodotto al carrello e applica il coupon.
1. Vai a **Estrai**.
1. Rendi il prodotto aggiunto &quot;esaurito&quot; prima di effettuare l’ordine.
1. Dovresti ricevere un errore *esaurito*.
1. Esegui cron.
1. Vai al carrello e rimuovi quel prodotto.
1. Aggiungi un altro prodotto e applica il coupon.

<u>Risultati previsti</u>:

Il codice del coupon deve essere applicato correttamente in quanto l’ordine precedente non è stato effettuato.

<u>Risultati effettivi</u>:

Si riceve un *codice coupon non valido* errore.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti a seconda del tipo di distribuzione:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
