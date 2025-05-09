---
title: 'MDVA-42410: nei report coupon viene visualizzata solo la valuta di base predefinita'
description: La patch MDVA-42410 risolve il problema relativo alla visualizzazione della sola valuta di base nei rapporti coupon. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12. L'ID della patch è MDVA-42410. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: b442a2ce-1bd4-4f09-95fd-2c626e32f509
feature: Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-42410: nei report coupon viene visualizzata solo la valuta di base predefinita

La patch MDVA-42410 risolve il problema relativo alla visualizzazione della sola valuta di base nei rapporti coupon. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12. L&#39;ID della patch è MDVA-42410. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Nei rapporti coupon viene visualizzata solo la valuta di base predefinita.

<u>Passaggi da riprodurre</u>:

1. Crea un ulteriore sito Web, store e vista store.
1. Imposta una valuta diversa per il nuovo sito Web. Ad esempio, Euro.
1. Vai a **Archivi** > **Tassi di valuta** e configura i tassi di valuta in **Euro**.
1. Crea una **Regola prezzo carrello** con un coupon specifico - **Test**.
1. Vai al front-end e inserisci un ordine con il coupon **Test** nel nuovo sito Web.
1. Vai a **Report** > **Vendite** > **Coupon**.
1. Seleziona il nuovo sito web nel menu a discesa Ambito.
1. Aggiornare le statistiche ed eseguire i rapporti.

<u>Risultati previsti</u>:

I rapporti coupon visualizzano la valuta del nuovo sito web come Euro.

<u>Risultati effettivi</u>:

La valuta di base predefinita (USD in questo caso) viene utilizzata nei rapporti coupon per il nuovo sito web.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella documentazione per gli sviluppatori.
