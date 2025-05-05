---
title: "MDVA-43605: i dati dell'ordine restituiscono valori negativi per i totali delle righe quando si utilizza l'API REST"
description: La patch MDVA-43605 risolve il problema per cui i dati dell'ordine restituiscono valori negativi per i totali delle righe quando si utilizza l'API Rest. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14. L'ID della patch è MDVA-43605. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: 8a679e85-1681-42c3-b072-18797198bdc4
feature: REST, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---

# MDVA-43605: i dati dell&#39;ordine restituiscono valori negativi per i totali delle righe quando si utilizza l&#39;API Rest

La patch MDVA-43605 risolve il problema per cui i dati dell&#39;ordine restituiscono valori negativi per i totali delle righe quando si utilizza l&#39;API Rest. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14. L&#39;ID della patch è MDVA-43605. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.1 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I dati dell’ordine restituiscono valori negativi per i totali delle righe quando si utilizza l’API Rest.

<u>Passaggi da riprodurre</u>:

1. Abilita spedizione gratuita.
1. Passa a **Configurazione** > **Catalogo** > **Prezzo** > e imposta Limite prezzo catalogo = Sito Web.
1. Passa a **Configurazione** > **Vendite** > **Imposta** e aggiorna:
   * Classe Imposta Per Spedizione = Merci Imponibili
   * Impostazioni di calcolo:
      * Prezzo catalogo = IVA inclusa
      * Prezzo di spedizione = prezzo incluso
      * Applicazione dello sconto sui prezzi = imposta inclusa
   * Impostazioni visualizzazione prezzo: IVA inclusa (tutti i campi)
   * Impostazioni di visualizzazione carrello acquisti: imposta inclusa (tutti i campi)
   * Ordini, fatture e note di accredito:
      * Visualizza importo spedizione = IVA inclusa
1. Crea un&#39;aliquota per US (Stato = &#39;*&#39;), Percentuale aliquota = 24,00
1. Creare una regola fiscale con l&#39;aliquota precedente.
1. Crea una regola di prezzo del carrello con un coupon specifico e Sconto = 50 $ dell&#39;importo fisso per l&#39;intero carrello.
1. Crea quattro prodotti con i seguenti prezzi: $ 8,90, $ 5,90, $ 6,90 e $ 5,95.
1. Crea un ordine di amministrazione che includa quattro di questi prodotti utilizzando il codice coupon creato nel passaggio precedente. Utilizza la spedizione gratuita.
1. Il pagamento non dovrebbe essere richiesto in quanto il codice della cedola copre il totale del carrello.
1. Recupera l’ordine appena creato tramite l’endpoint API REST:

   ```json
   GET rest/V1/orders/1
   ```

<u>Risultati previsti</u>:

I valori di `base_row_total` e `base_row_total_incl_tax` nella risposta sono zero.

<u>Risultati effettivi</u>:

I campi `base_row_total` e `base_row_total_incl_tax` nella risposta hanno valori negativi.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella documentazione per gli sviluppatori.
