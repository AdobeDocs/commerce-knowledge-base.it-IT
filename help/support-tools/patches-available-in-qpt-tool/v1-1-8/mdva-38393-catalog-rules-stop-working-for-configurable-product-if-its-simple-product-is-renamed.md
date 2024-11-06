---
title: "MDVA-38393: le regole del catalogo cessano di funzionare per il prodotto configurabile se il relativo prodotto semplice viene rinominato"
description: La patch MDVA-38393 risolve il problema che causa il mancato funzionamento delle regole di catalogo per un prodotto configurabile se il relativo prodotto semplice viene rinominato. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8. L'ID della patch è MDVA-38393. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
exl-id: a20856c4-8aff-427b-a404-7afe706be06f
feature: Catalog Management, Categories, Configuration, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# MDVA-38393: le regole del catalogo cessano di funzionare per il prodotto configurabile se il relativo prodotto semplice viene rinominato

La patch MDVA-38393 risolve il problema che causa il mancato funzionamento delle regole di catalogo per un prodotto configurabile se il relativo prodotto semplice viene rinominato. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8. L&#39;ID della patch è MDVA-38393. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le regole del catalogo cessano di funzionare per un prodotto configurabile se il relativo prodotto semplice viene rinominato.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto configurabile con un prodotto semplice associato.
1. Crea una categoria.
1. Assegna solo il prodotto configurabile alla nuova categoria.
1. Crea nuove regole catalogo:
   * Condizione = La categoria contiene \&lt;new category id>
   * Azione = sconto del 50%
   * Attivo = Sì
1. Eseguire la reindicizzazione.
1. Controlla il prodotto configurabile sul front-end (deve essere applicato lo sconto).
1. Controllare la tabella `catalogrule_product` (il prodotto semplice deve avere uno sconto).
1. Vai all’amministratore e modifica il nome del prodotto semplice. Questo aggiungerebbe un record alla tabella `catalogrule_product_cl`.
1. Eseguire il cron o il comando `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1`.
1. Controllare la tabella `catalogrule_product`.

<u>Risultati previsti</u>:

Il prodotto configurabile ha uno sconto.

<u>Risultati effettivi</u>:

* Nella tabella `catalogrule_product` mancano i record di sconto creati per i prodotti semplici.
* Il prodotto configurabile sul front-end ha il prezzo originale completo.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella documentazione per gli sviluppatori.
