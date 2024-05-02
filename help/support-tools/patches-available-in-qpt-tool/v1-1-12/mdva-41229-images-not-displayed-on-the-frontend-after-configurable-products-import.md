---
title: "MDVA-41229: le immagini disponibili nel back-end non vengono visualizzate nel front-end dopo l’importazione di prodotti configurabili"
description: La patch MDVA-41229 risolve il problema per cui le immagini disponibili sul back-end non vengono visualizzate sul front-end dopo l’importazione di prodotti configurabili. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12. L'ID della patch è MDVA-41229. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: 69d7374f-9f8b-4ec4-8a7f-135ee06135a3
feature: Data Import/Export, Configuration, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '688'
ht-degree: 2%

---

# MDVA-41229: le immagini disponibili nel back-end non vengono visualizzate nel front-end dopo l’importazione di prodotti configurabili

La patch MDVA-41229 risolve il problema per cui le immagini disponibili sul back-end non vengono visualizzate sul front-end dopo l’importazione di prodotti configurabili. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12. L&#39;ID della patch è MDVA-41229. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.2-p2 e 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le immagini disponibili sul backend non vengono visualizzate sul front-end dopo l’importazione di prodotti configurabili.

<u>Passaggi da riprodurre</u>:

1. Installa un Adobe Commerce pulito.
1. Aggiungi un attributo personalizzato andando in **Negozi** > **Attributi** > **Prodotto** > **Aggiungi nuovo attributo** con le impostazioni seguenti:
   * Proprietà:
      * Proprietà attributo:
         * Etichetta predefinita: Imposta dimensione
         * Tipo di input del catalogo per il proprietario del negozio: campione di testo
         * Valori richiesti: no
         * Aggiorna immagine anteprima prodotto: sì
      * Gestisci campione (valori dell&#39;attributo):

        | È predefinito | Campione amministratore | Descrizione amministratore | Campione visualizzazione store predefinito | Descrizione predefinita vista store |
        |---|---|---|---|---|
        | no | 4 | 4 | 4 | 4 |
        | no | 24 | 24 | 24 | 24 |
        | no | 30 | 30 | 30 | 30 |
        | no | 60 | 60 | 60 | 60 |
        | no | 68 | 68 | 68 | 68 |
      * Proprietà attributi avanzate:
         * Codice attributo: set_size
         * Ambito: globale
         * Valore univoco: No
         * Convalida input per proprietario archivio: nessuna
         * Opzioni Aggiungi a colonna: No
         * Usa in opzioni filtro: No
   * Gestisci etichette:
      * Gestione titoli (dimensioni, colore, ecc.)
         * Visualizzazione store predefinita: Imposta dimensione
   * Proprietà vetrina:
      * Usa nella ricerca: Sì
      * Peso ricerca: 1
      * Visibile in Ricerca avanzata: no
      * Confrontabile su Storefront: sì
      * Usa in navigazione a livelli: filtrabile (con risultati)
      * Usa in navigazione a livelli dei risultati di ricerca: Sì
      * Usa per condizioni regola promozionale: no
      * Visibile sulle pagine del catalogo in Storefront: sì
      * Utilizzato nell’elenco dei prodotti: sì
      * Utilizzato per l’ordinamento nell’elenco dei prodotti: no
1. Aggiungi questo attributo al set di attributi predefinito nel gruppo Dettagli prodotto (**Negozi** > **Attributi** > **Set di attributi**).
1. Scarica le immagini impostate nella cartella var all’interno della directory principale di Adobe Commerce.
1. Vai a **Sistema** > **Trasferimento dati** > e importare il file utilizzando le opzioni seguenti:
   * Importa impostazioni:
      * Tipo di entità: prodotti
   * Comportamento importazione:
      * Comportamento di importazione: Aggiungi/Aggiorna
      * Strategia di convalida: arresto in caso di errore
      * Conteggio errori consentiti: 1
      * Separatore campi: `;`
      * Separatore di più valori: `,`
      * Costante valore attributo: EMPTYVALUE
      * Campi allegati: deselezionato
   * File da importare:
      * Selezionate il file da importare
      * Directory file immagini: lasciate vuoto
1. Vai alla vetrina per `/product-set.html` e passare da un formato all&#39;altro. Per Set Size 24, non ci sarà alcuna galleria.

<u>Risultati previsti</u>:

La galleria di tutti i prodotti semplici all’interno di un prodotto configurabile è visibile con tutte le immagini correlate.

<u>Risultati effettivi</u>:

Non ci sono gallerie per i prodotti.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
