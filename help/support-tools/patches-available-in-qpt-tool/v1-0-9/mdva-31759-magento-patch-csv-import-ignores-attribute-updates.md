---
title: "Patch MDVA-31759: l'importazione CSV ignora gli aggiornamenti degli attributi"
description: La patch MDVA-31759 risolve il problema relativo all'importazione del file CSV, in cui gli attributi aggiuntivi vengono ignorati con i tipi *A discesa* e *Area testo*. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9. Il problema è stato risolto in Adobe Commerce 2.4.2.
exl-id: 5426866c-893f-4abe-bfbc-6e7b30dd8dab
feature: Attributes, Data Import/Export
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# Patch MDVA-31759: l&#39;importazione CSV ignora gli aggiornamenti degli attributi

La patch MDVA-31759 risolve il problema relativo all&#39;importazione CSV in cui gli attributi aggiuntivi vengono ignorati con *A discesa* e *Area di testo* tipi. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9. Il problema è stato risolto in Adobe Commerce 2.4.2.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.4.0

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud e Adobe Commerce on-premise 2.3.0 - 2.4.1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’importazione CSV ignora gli attributi aggiuntivi con *A discesa* e *Area di testo* tipi.

<u>Passaggi da riprodurre</u>:

1. Accedi all’amministratore di Commerce.
1. Crea un attributo di prodotto con la seguente configurazione:
   * **Etichetta predefinita**: *G003*
   * **Tipo di input del catalogo per il proprietario del negozio**: *Area di testo* o *A discesa*
   * **Codice attributo**: *G003*
   * **Ambito**: *Globale*
1. Aggiungi l&#39;attributo precedente al set di attributi predefinito.
1. Crea un prodotto con il set di attributi predefinito e specifica un valore per il nuovo attributo.
1. Esporta il prodotto in formato CSV.
1. Aggiornare il valore dell’attributo in **additional\_attributes** colonna.
1. Importa il file CSV aggiornato.

<u>Risultati previsti</u>:

Il valore dell’attributo G003 viene aggiornato.

<u>Risultati effettivi</u>:

Il valore dell&#39;attributo G003 non è aggiornato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
