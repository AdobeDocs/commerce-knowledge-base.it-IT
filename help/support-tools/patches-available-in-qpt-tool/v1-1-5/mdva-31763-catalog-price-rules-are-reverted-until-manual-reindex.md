---
title: 'MDVA-31763: le regole dei prezzi del catalogo vengono ripristinate fino alla reindicizzazione manuale'
description: La patch di MDVA-31763 risolve il problema del ripristino delle regole dei prezzi di catalogo fino alla reindicizzazione manuale. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5. L'ID della patch è MDVA-31763. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
exl-id: eb2dfd1a-6d12-4676-82c1-bf92c6fa9fda
feature: Catalog Management, Orders, Price Rules
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# MDVA-31763: le regole dei prezzi del catalogo vengono ripristinate fino alla reindicizzazione manuale

La patch di MDVA-31763 risolve il problema del ripristino delle regole dei prezzi di catalogo fino alla reindicizzazione manuale. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5. L&#39;ID della patch è MDVA-31763. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando l&#39;indicizzatore parziale `catalogrule_product` viene eseguito su prodotti configurabili, le regole del catalogo scompaiono.

<u>Passaggi da riprodurre</u>:

1. Accedi al backend di amministrazione.
1. Vai a **Archivi** > **Attributi** > **Prodotto** e cerca l&#39;attributo &quot;produttore&quot;.
   * Aggiungi alcune opzioni e imposta &quot;Usa per le condizioni delle regole promozionali&quot; su *Sì*.
1. Vai a **Archivi** > **Attributi** > **Set di attributi**.
   * Selezionare il set di attributi predefinito e aggiungervi l&#39;attributo &quot;produttore&quot;.
1. Crea un prodotto configurabile con un paio di varianti.
1. Imposta il valore dell’attributo &quot;produttore&quot; per il prodotto configurabile creato in precedenza.
1. Creare regole di catalogo:
   * Attivo = Sì
   * Siti Web = Sito Web principale
   * Gruppi di clienti = NON CONNESSO
   * Condizioni: produttore = \&lt;valore selezionato per il prodotto configurabile>
   * Azioni: qualsiasi sconto
1. Eseguire un indice completo.
1. Controlla il prezzo del prodotto su PDP e assicurati che il prezzo sia corretto.
1. Aggiorna l’attributo &quot;weight&quot; del prodotto configurabile creato.
1. Verifica il prezzo del prodotto su PDP.

<u>Risultati previsti</u>:

Le regole del prezzo di catalogo impostate sui prodotti configurabili non vengono rimosse durante la reindicizzazione parziale.

<u>Risultati effettivi</u>:

Le regole del prezzo di catalogo impostate sui prodotti configurabili scompaiono durante la reindicizzazione parziale.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
