---
title: "MDVA-31295: punti fedeltà su ordini parziali"
description: La patch di MDVA-31295 risolve il problema relativo al calcolo errato dei punti premio al completamento di un ordine parziale e alla tassazione degli elementi. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8. Il problema è stato risolto in Adobe Commerce 2.4.2.
exl-id: 10e8a3a9-bfab-4256-b772-fd64e8885da3
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# MDVA-31295: punti fedeltà su ordini parziali

La patch di MDVA-31295 risolve il problema relativo al calcolo errato dei punti premio al completamento di un ordine parziale e alla tassazione degli elementi. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8. Il problema è stato risolto in Adobe Commerce 2.4.2.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce on-premise 2.3.0

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I premi non vengono applicati ai conti dei clienti quando l&#39;ordine è completo (parzialmente spedito) e gli articoli vengono tassati. Quando gli elementi non vengono tassati, i premi vengono aggiunti correttamente agli account dei clienti.

<u>Passaggi da riprodurre</u>:

1. Accedi a storefront come cliente.
1. Aggiungi due prodotti al carrello.
1. Vai a pagamento, imposta l&#39;indirizzo di spedizione che ha le imposte, e inserisci l&#39;ordine.
1. Nell’amministratore, passa all’ordine inserito di recente.
1. Fare clic su **Fattura** e impostare **Qtà su Fattura** su 0 per uno degli elementi, quindi fare clic su **Aggiorna Qtà**. Invia fattura.
1. Fare clic su Spedisci e impostare **Qtà da spedire** su 0 per l&#39;articolo non fatturato. Fare clic su **Invia spedizione**.
1. Fare clic su Annulla ordine. Lo stato viene impostato su Completato.
1. Nell&#39;amministratore, vai a **Clienti** > Scegli l&#39;acquisto del cliente effettuato prima di > **Punti premio** > **Cronologia punti premio**.
1. Controlla i punti premio guadagnati per l&#39;ordine effettuato.

<u>Risultati previsti</u>:

I punti premio devono essere calcolati per gli ordini imponibili al completamento di un ordine parziale.

<u>Risultati effettivi</u>:

I punti premio non vengono calcolati per un ordine imponibile al completamento di un ordine parziale.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
