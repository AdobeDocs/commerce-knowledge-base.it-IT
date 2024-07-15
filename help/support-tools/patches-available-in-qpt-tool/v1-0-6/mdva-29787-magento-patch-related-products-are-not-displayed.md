---
title: "MDVA-29787: i prodotti correlati non vengono visualizzati"
description: La patch MDVA-29787 risolve il problema che impedisce la visualizzazione di **Prodotti correlati** in un front-end di un archivio Adobe Commerce. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6. L'ID della patch è MDVA-29787.
exl-id: ee060d7b-3b0e-4bd5-84e6-fbd6d2fa532f
feature: Cache, Marketing Tools, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 0%

---

# MDVA-29787: i prodotti correlati non vengono visualizzati

La patch MDVA-29787 risolve il problema che impedisce la visualizzazione di **Prodotti correlati** in un front-end di un archivio Adobe Commerce. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6. L&#39;ID della patch è MDVA-29787.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce sull’infrastruttura cloud 2.3.3.

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.0.

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La regola di destinazione per **Prodotti correlati** non funziona se &quot;*è una delle*&quot; condizioni utilizzate per **Prodotti da visualizzare** nell&#39;amministrazione di Commerce.

>[!NOTE]
>
>Nota: questa patch non corregge le regole di destinazione esistenti. È necessario ricreare le regole di destinazione esistenti.

<u>Passaggi da riprodurre</u>:

1. Crea **Nuovo Attributo** (Esempio: Test\_Attr).
   * Imposta **Tipo di input catalogo per il proprietario dell&#39;archivio** = *Testo.*
   * In **Proprietà vetrina**, impostare **Usa per le condizioni della regola promozionale** = *Sì*.
1. Crea **Nuovo Set Di Attributi** (Esempio: Test\_Set).
1. Aggiungere il **nuovo attributo** al **nuovo set di attributi** (esempio: aggiungere l&#39;attributo &quot;Test\_Attr&quot; al set di attributi &quot;Test\_Set&quot;).
1. Crea tre prodotti. Nell’esempio, sono impostati come segue:
   * Product1, Test\_Attr = MAGT2NA\_Test3
   * Product2, Test\_Attr = 24-MB02
   * Prodotto3, Test\_Attr = 701644329389M
1. Crea **Regola** di destinazione (**Marketing**   > **Regole prodotto correlate** e fare clic sul pulsante **Aggiungi regola**.) con impostazioni:
   * **Applica a** = *Prodotti correlati*
   * **Prodotti corrispondenti**
   * Imposta il nuovo attributo creato **in** **Passaggio 1 sopra** come attributo di Product1 (esempio: Test\_Attr = MAGT2NA\_Test3).
   * **Prodotti da visualizzare** = Attributi degli altri due prodotti (ad esempio: attributi 24-MB02 e 701644329389M).
1. Salva la **regola**.
1. Esegui una reindicizzazione, se necessario.
1. Cancella cache.
1. Apri Product1 sul front-end.

<u>Risultati previsti</u>:

Sono presenti i prodotti correlati.

<u>Risultati effettivi</u>:

Mancano i prodotti correlati.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
