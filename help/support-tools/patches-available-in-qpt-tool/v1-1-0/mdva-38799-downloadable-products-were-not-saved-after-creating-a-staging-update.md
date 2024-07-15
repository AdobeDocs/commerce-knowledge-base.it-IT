---
title: "MDVA-38799: prodotti scaricabili non salvati dopo la creazione di un aggiornamento di staging"
description: La patch MDVA-38799 risolve il problema che impedisce il salvataggio dei prodotti scaricabili dopo la creazione di un aggiornamento di staging. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.0. L'ID della patch è MDVA-38799. Il problema è stato risolto nella versione 2.4.3 di Adobe Commerce.
exl-id: 306f9ef3-ca3a-41b9-a5d3-42aa4ef59953
feature: Products, Staging
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# MDVA-38799: prodotti scaricabili non salvati dopo la creazione di un aggiornamento di staging

La patch MDVA-38799 risolve il problema che impedisce il salvataggio dei prodotti scaricabili dopo la creazione di un aggiornamento di staging. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.0. L&#39;ID della patch è MDVA-38799. Il problema è stato risolto nella versione 2.4.3 di Adobe Commerce.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce sull’infrastruttura cloud 2.4.1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0-2.4.2-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I prodotti scaricabili non vengono salvati dopo la creazione di un aggiornamento di staging. Gli utenti ricevono il messaggio di errore: *L&#39;esempio scaricabile non è correlato al prodotto. Verifica il collegamento e riprova*.

<u>Passaggi da riprodurre</u>:

1. Passa a **Catalogo** > **Prodotti**.
1. Fai clic sul menu a discesa accanto a Aggiungi prodotto e seleziona Prodotto scaricabile.
   * Compila il nome, lo SKU, il prezzo e la quantità del prodotto.
1. Scorri fino alla pagina Informazioni scaricabili.
1. In Esempi fare clic su **Aggiungi collegamento**.
   * Compila il Titolo, Carica file (il tipo di file non conta).
1. Fai clic su **Salva**. Verrà visualizzato il seguente messaggio: *Il prodotto è stato salvato*.
1. Fai clic su **Pianifica nuovo aggiornamento** nella parte superiore della pagina.
   * Compila il Nome aggiornamento e una Data inizio e una Data fine legali.
1. Fai clic su **Salva** nell&#39;aggiornamento dell&#39;area di gestione temporanea.
1. Fai clic su **Salva** sul prodotto.

<u>Risultati previsti</u>:

Il prodotto viene salvato senza errori.

<u>Risultati effettivi</u>:

Viene visualizzato il messaggio di errore: *L&#39;esempio scaricabile non è correlato al prodotto. Verifica il collegamento e riprova*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
