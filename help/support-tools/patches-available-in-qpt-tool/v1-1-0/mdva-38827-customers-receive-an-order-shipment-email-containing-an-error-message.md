---
title: "MDVA-38827: i clienti ricevono un errore di spedizione ordine tramite e-mail"
description: "La patch di MDVA-38827 risolve il problema relativo alla ricezione da parte dei clienti di un'e-mail di spedizione dell'ordine contenente il seguente messaggio di errore: *Si è verificato un errore durante la generazione di questo contenuto*. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.0. L'ID della patch è MDVA-38827. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.4."
exl-id: f2e5aeab-7d46-46be-9631-c3a863d9bf52
feature: Communications, Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# MDVA-38827: i clienti ricevono un errore di spedizione ordine tramite e-mail

La patch di MDVA-38827 risolve il problema relativo alla ricezione da parte dei clienti di un messaggio di posta elettronica di spedizione dell&#39;ordine contenente il seguente messaggio di errore: *Si è verificato un errore durante la generazione del contenuto*. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.0. L&#39;ID della patch è MDVA-38827. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.4.2-p1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.3-p1 - 2.4.2-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando è selezionata l’opzione Notifica ai clienti per e-mail per la spedizione, i clienti ricevono un messaggio e-mail contenente il seguente messaggio di errore: *Si è verificato un errore durante la generazione del contenuto*.

<u>Passaggi da riprodurre</u>:

1. Vai a **Marketing** > **Comunicazioni** > **Modelli e-mail** e seleziona **Aggiungi nuovo modello**.
   * Seleziona **Vendite Magento** > **Nuova spedizione**.
   * Fai clic su **Carica modello**.
   * Aggiungi un nome modello (ad esempio, Modello di spedizione principale) e fai clic su **Salva**.
1. Vai a **Archivia** > Impostazioni > **Configurazione** > **Vendite** > **E-mail vendita**:
   * Abilita **Commenti spedizione**.
   * Seleziona **Modello di spedizione principale** (fare riferimento alla parte &quot;Aggiungere un nome di modello&quot; del passaggio 1) in Modello e-mail commento spedizione e Modello e-mail commento spedizione per ospite.
1. Effettua un ordine. Vai al pannello di amministrazione > **Vendite** > **Ordine**, fai clic su **Visualizza** e quindi spedire l&#39;ordine.
1. Lo stato dell’ordine passerà da In sospeso a In elaborazione.
1. Clic **Spedizioni** dal menu della barra laterale a sinistra, quindi fai clic su **Visualizza** per vedere l&#39;ordine.
1. Aggiungi un commento in **Testo commento** sotto **Cronologia spedizione** e seleziona la casella di controllo **Notifica al cliente via e-mail**.
1. Clic **Invia commento**.

<u>Risultati previsti</u>:

Viene generato un messaggio e-mail di vendita con commenti sulla spedizione.

<u>Risultati effettivi</u>:

Nell’e-mail viene ricevuto il seguente messaggio di errore: *Si è verificato un errore durante la generazione del contenuto.*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
