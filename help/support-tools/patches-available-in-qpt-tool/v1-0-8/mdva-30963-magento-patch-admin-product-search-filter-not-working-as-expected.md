---
title: "MDVA-30963: il filtro di ricerca dei prodotti di amministrazione non funziona come previsto"
description: La patch MDVA-30963 risolve il problema che causa il mancato funzionamento del filtro di ricerca dei prodotti e dell'amministratore di Commerce. I valori che vengono sostituiti in un ambito di visualizzazione archivio vengono considerati anche quando si applica un filtro all'ambito di visualizzazione **Tutte le visualizzazioni archivio**. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8. Il problema è stato risolto in Adobe Commerce 2.4.2.
exl-id: bde2836e-8954-48e5-b411-08c951ec8620
feature: Admin Workspace, Products, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 0%

---

# MDVA-30963: il filtro di ricerca dei prodotti di amministrazione non funziona come previsto

La patch MDVA-30963 risolve il problema che causa il mancato funzionamento del filtro di ricerca dei prodotti e dell&#39;amministratore di Commerce. I valori che vengono sostituiti in un ambito di visualizzazione archivio vengono considerati anche quando si applica il filtro **Tutte le visualizzazioni store** archiviare l&#39;ambito di visualizzazione. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8. Il problema è stato risolto in Adobe Commerce 2.4.2.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce sull’infrastruttura cloud 2.4.0

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.2 - 2.4.1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Passaggi da riprodurre</u>:

1. Imposta **Negozi** > **Configurazione** > **Catalogo** > **Catalogo** > **Prezzo** > **Ambito prezzo catalogo** = *Sito Web*.
1. Crea due siti Web con due valute diverse (ad esempio, il sito Web predefinito è India Store \[Rupee ₹\] e il secondo è US Store \[Dollaro $\]).
1. Imposta quanto segue **Valuta di base**, **Valuta di visualizzazione predefinita**, e **Valute consentite**:
   * **Configurazione predefinita** = *Dollaro USA (predefinito)*
   * **Sito Web principale** = *Rupia indiana*
   * **Sito WebUS** = **Usa predefinito** = *Dollaro USA*
1. Imposta **Negozi** > **Tassi di cambio** = *1:1*.
1. Crea un prodotto semplice di test assegnato a entrambi i siti Web con i seguenti prezzi:
   * **Prezzo predefinito** = **Prezzo per sito Web USA** = *123 USD*
   * **Prezzo principale del sito web** = *Rupia 321*
1. Crea un utente subAdmin con accesso solo allo Store USA.
1. Vai alla vetrina negli Stati Uniti e inserisci un prodotto nel carrello (Esempio: *Prezzo USD 123*).
1. Accedi all’amministratore con il sottoamministratore appena creato (esempio: *Amministratore solo Stati Uniti*).
1. Vai a **Rapporti** > **Prodotti nel carrello**.

<u>Risultati previsti</u>:

Quando si filtra all’interno di **Tutte le visualizzazioni store** archiviare l’ambito di visualizzazione, il filtro prodotti deve ottenere il valore impostato in tale ambito particolare.

<u>Risultati effettivi</u>:

I valori sostituiti in un ambito di visualizzazione archivio vengono considerati anche quando si applica un filtro all’ambito di visualizzazione archivio &quot;Tutte le visualizzazioni archivio&quot;.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
