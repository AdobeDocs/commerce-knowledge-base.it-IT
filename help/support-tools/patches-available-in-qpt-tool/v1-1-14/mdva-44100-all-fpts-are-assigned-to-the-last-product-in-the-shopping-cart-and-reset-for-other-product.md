---
title: "MDVA-44100: tutti gli FPT sono assegnati all’ultimo prodotto nel carrello"
description: La patch MDVA-44100 risolve il problema in cui tutti gli FPT vengono assegnati all’ultimo prodotto nel carrello. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14. L'ID della patch è MDVA-44100. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: ab0f195c-fcc6-41ac-932d-d2603d068aa6
feature: Orders, Products, Shopping Cart
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-44100: tutti gli FPT vengono assegnati all’ultimo prodotto nel carrello

La patch MDVA-44100 risolve il problema in cui tutti gli FPT vengono assegnati all’ultimo prodotto nel carrello. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14. L&#39;ID della patch è MDVA-44100. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Tutti gli FPT vengono assegnati all’ultimo prodotto nel carrello e i valori FPT per gli altri prodotti vengono reimpostati.

<u>Passaggi da riprodurre</u>:

1. Vai a **Negozi** > **Configurazione** > **Vendite** > **Imposta** e imposta:
   * Abilita FPT = Sì
   * Applica imposta a FPT = Sì
   * Includi FPT nel subtotale = Sì
1. Vai a **Archivi** > **Attributo** > **Prodotto** e crea un nuovo attributo con tipo = Imposta sul prodotto fissa.
1. Aggiungere l&#39;attributo a un set di attributi.
1. Crea due prodotti dal set di attributi e configura l’attributo FPT per il paese e lo stato.
1. Aggiungi entrambi gli elementi all&#39;ordine.
1. Immettere un indirizzo che richiede il pagamento di un FPT.
1. Effettua l’ordine.
1. Controllare l&#39;elenco degli articoli nell&#39;ordine.

<u>Risultati previsti</u>:

Gli FPT vengono visualizzati sotto ogni prodotto.

<u>Risultati effettivi</u>:

I valori FPT di entrambi gli elementi sono mostrati sotto il secondo elemento.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella documentazione per gli sviluppatori.
