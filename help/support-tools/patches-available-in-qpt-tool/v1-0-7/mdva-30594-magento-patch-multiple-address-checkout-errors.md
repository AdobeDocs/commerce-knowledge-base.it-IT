---
title: "MDVA-30594: errori di checkout di più indirizzi"
description: La patch di MDVA-30594 risolve il problema relativo alla mancata visualizzazione della pagina di completamento dell'ordine dopo l'inserimento di un ordine con più indirizzi. Il controllo degli ordini in Commerce Admin mostra due ordini con gli stessi prodotti invece dei prodotti corretti. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7. Il problema è stato risolto in Adobe Commerce 2.4.2.
exl-id: 7560cc39-ff0d-4313-979e-5cd588554c1d
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 0%

---

# MDVA-30594: errori di checkout di più indirizzi

La patch di MDVA-30594 risolve il problema relativo alla mancata visualizzazione della pagina di completamento dell&#39;ordine dopo l&#39;inserimento di un ordine con più indirizzi. Il controllo degli ordini in Commerce Admin mostra due ordini con gli stessi prodotti invece dei prodotti corretti. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7. Il problema è stato risolto in Adobe Commerce 2.4.2.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce sull’infrastruttura cloud 2.3.3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli ordini con più indirizzi non vengono completati con la pagina di successo dell’ordine e mostrano due ordini con gli stessi prodotti invece di quelli corretti.

<u>Prerequisiti</u>:

Crea due siti Web con store e visualizzazioni dello store.

<u>Passaggi da riprodurre</u>:

1. Imposta **Ambito prezzo catalogo** per il catalogo del sito Web (**Archivi** > **Impostazioni** > **Configurazione** > **Catalogo** > **Catalogo** > **Prezzo** > **Ambito**).
1. Configura **imposte sui prodotti fisse** (**Negozi** > **Configurazione** > **Vendite** > **Imposta** > **Imposte sui prodotti fisse**):

   * **Abilita FPT** = *Sì*
   * **Visualizza prezzi nell&#39;elenco prodotti** = *Escluso FPT*
   * **Visualizza prezzi nella pagina di visualizzazione del prodotto** = *FPT escluso*
   * **Visualizza prezzi nei moduli di vendita** = *Escluso FPT* (inclusa la descrizione di **FPT** e il prezzo finale).
   * **Visualizza prezzi nelle e-mail** = *Escluso FPT* (inclusa la descrizione di **FPT** e il prezzo finale).
   * **Applica imposta a FPT** = *Sì*
   * **Includi FPT nel subtotale** = *No*

1. Creare un attributo **FPT** e assegnarlo al set di attributi predefinito. (Vedi [Configurazione di FPT: creazione di un attributo FPT](https://docs.magento.com/user-guide/tax/fixed-product-tax-configuration.html#step-2-create-an-fpt-attribute) nella guida utente).

1. Crea quattro prodotti semplici e imposta il valore **FPT** **attribute** (esempio: imposta il **FPT**   **valore attributo** = *Australia*).

1. Crea due prodotti in bundle con la seguente configurazione:

   * Definisci **FPT**.
   * Imposta **Prezzo dinamico** = *No*.
   * Imposta **Prezzo** = *100*.
   * Opzioni bundle fornite insieme, tutte contrassegnate come predefinite con **Tipo di prezzo** = *Fisso*.
   * Aggiungi due dei prodotti semplici creati nel passaggio quattro.

1. Crea un account utente nel front-end. Aggiorna l&#39;indirizzo con l&#39;indirizzo australiano (imposta il paese su Australia o su qualsiasi paese utilizzato nella configurazione di **FPT**).

1. Aggiungi i due prodotti nel carrello.

1. Vai alla pagina del carrello e verifica che il **FPT** sia visualizzato correttamente.

1. Fare clic su **Estrai con più indirizzi**.

1. Aggiungi un secondo indirizzo.

1. Assegna ogni prodotto a un indirizzo diverso.

1. Continua con il processo di pagamento fino a **Inserisci ordine**.

1. Fai clic sul pulsante **Inserisci ordine**.

<u>Risultati previsti</u>:

L’ordine con più indirizzi viene effettuato correttamente.

<u>Risultati effettivi</u>:

Messaggio di tipo &quot;*Errore.*&quot; verrà visualizzato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
