---
title: "MDVA-30837: importo minimo per la spedizione gratuita"
description: La patch MDVA-30837 aggiunge opzioni di configurazione per il calcolo della spedizione gratuita in modo che l'utente possa configurare l'importo minimo dell'ordine per ottenere la spedizione gratuita in base al subtotale (o totale complessivo). Ciò consente personalizzazioni locali per i metodi di imposta e spedizione. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7. Il problema è stato risolto in Adobe Commerce 2.4.2.
exl-id: 64716d08-4ce0-40d5-aeb7-242e2aa85bb0
feature: Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 0%

---

# MDVA-30837: importo minimo per la spedizione gratuita

La patch MDVA-30837 aggiunge opzioni di configurazione per il calcolo della spedizione gratuita in modo che l&#39;utente possa configurare l&#39;importo minimo dell&#39;ordine per ottenere la spedizione gratuita in base al subtotale (o totale complessivo). Ciò consente personalizzazioni locali per i metodi di imposta e spedizione. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7. Il problema è stato risolto in Adobe Commerce 2.4.2.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce sull’infrastruttura cloud 2.3.4-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce sull’infrastruttura cloud 2.3.1 - 2.3.4-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La patch MDVA-30837 aggiunge l&#39;impostazione di configurazione per configurare l&#39;impostazione **Importo ordine minimo** per ottenere la spedizione gratuita in base al subtotale (o totale complessivo):

* **Includi imposta nell&#39;importo**: *Sì/No* nella configurazione del metodo di spedizione gratuita.
   * Quando **Includi imposta in importo** è impostato su *Sì*, l&#39;importo minimo dell&#39;ordine viene calcolato come Subtotale + Imposta - Sconto.
   * Quando **Includi imposta in importo** è impostato su *No*, l&#39;importo minimo dell&#39;ordine viene calcolato come Subtotale - Sconto.

<u>Passaggi da riprodurre</u>:

1. Vai a **Archivi** > Impostazioni > **Configurazione** > **Vendite** > **Imposta** e imposta quanto segue:

   * Calcolo imposta basato su *Indirizzo di spedizione*
   * Abilita commercio transfrontaliero: *No*
   * Visualizza prezzi prodotti nel catalogo: *IVA esclusa*
   * Visualizza prezzi di spedizione: *IVA esclusa*
   * Visualizza prezzi: *IVA esclusa*
   * Visualizza Subtotale: *Imposta esclusa*
   * Visualizza importo spedizione: *IVA esclusa*
   * Visualizza prezzi per confezione regalo: *IVA esclusa*
   * Visualizza prezzi carta stampata: *IVA esclusa*
   * Includi imposta nel totale ordine: *Sì*
   * Visualizza riepilogo imposte completo: *Sì*

1. Vai a **Vendite** > **Impostazioni spedizione** > **Spedizione gratuita** e imposta **Importo ordine minimo** = *30*.
1. Vai a **Marketing** > Promozioni > **Regole prezzo carrello** e crea una nuova regola prezzo (per i passaggi dettagliati, consulta [Creare una regola prezzo carrello](https://docs.magento.com/user-guide/marketing/price-rules-cart-create.html) nella nostra guida utente).

   * Codice coupon = *Coupon specifico*.
   * Condizioni: il subtotale è uguale o superiore a 25 $.
   * Azioni: Spedizione gratuita = *Per spedizioni con articoli corrispondenti*.

1. Crea un prodotto al prezzo di 23,10 $.
1. Aggiungere l&#39;imposta CA alla regola fiscale predefinita.
1. Aggiungi questo prodotto al carrello.
1. Ottieni un preventivo di spedizione: al netto delle imposte, il totale complessivo = $ 25,01 e viene applicata la spedizione gratuita.
1. Applica il codice coupon: non sarà valido perché il Subtotale (IVA esclusa) è di $ 23,10.

<u>Risultati previsti</u>:

È presente un&#39;impostazione di configurazione aggiuntiva. Includi imposta nell&#39;importo: *Sì*/*No* nella configurazione del metodo di spedizione gratuita:

* Quando Includi imposta in importo è impostato su *Sì*, l&#39;importo ordine minimo viene calcolato come Subtotale + Imposta - Sconto.
* Quando Includi importo imposta è impostato su *No*, l&#39;importo minimo dell&#39;ordine viene calcolato come Subtotale - Sconto.

<u>Risultati effettivi</u>:

La condizione della regola del prezzo di spedizione gratuito può essere basata solo sul subtotale, mentre il metodo di spedizione gratuita può essere basato solo sul totale complessivo.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
