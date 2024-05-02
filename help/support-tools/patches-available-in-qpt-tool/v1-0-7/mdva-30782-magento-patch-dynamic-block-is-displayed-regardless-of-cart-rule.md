---
title: "MDVA-30782: il blocco dinamico viene visualizzato indipendentemente dalla regola del carrello"
description: La patch MDVA-30782 risolve il problema della visualizzazione di un blocco dinamico indipendentemente dalla regola del carrello. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7. Il problema è stato risolto in Adobe Commerce 2.4.2.
exl-id: 88da8853-aae7-4fd9-82ba-a4e9fc99cf53
feature: Cache, Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# MDVA-30782: il blocco dinamico viene visualizzato indipendentemente dalla regola carrello

La patch MDVA-30782 risolve il problema della visualizzazione di un blocco dinamico indipendentemente dalla regola del carrello. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7. Il problema è stato risolto in Adobe Commerce 2.4.2.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.5-p1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.5 - 2.4.2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il blocco dinamico viene visualizzato nella pagina anche quando la condizione della regola del prezzo di catalogo correlata non è soddisfatta.

<u>Passaggi da riprodurre</u>:

1. Crea due prodotti.
1. Crea una regola del prezzo di catalogo applicabile solo a uno di questi prodotti.
1. Crea un blocco dinamico e assegna ad esso la regola del prezzo di catalogo appena creata.
1. Crea un widget con i seguenti parametri:
   * Tipo = Rotatore a blocchi dinamici
   * Blocchi dinamici da visualizzare = Blocchi dinamici specificati
   * Specifica blocchi dinamici = passaggio modulo blocco \#3Layout Aggiornamenti (può essere qualsiasi)
   * Visualizza su = Tutti i tipi di prodotto
   * Contenitore = Informazioni ausiliarie prodotto
1. Esegui la reindicizzazione e svuota la cache.
1. Verifica la presenza di un modulo a blocchi dinamici in entrambe le pagine di prodotto \#3

<u>Risultati previsti</u>:

Il blocco dinamico viene visualizzato solo nella prima pagina di prodotto.

<u>Risultati effettivi</u>:

Il blocco dinamico viene visualizzato su entrambe le pagine di prodotto. Con Blocchi dinamici da visualizzare = Regola prezzo catalogo correlata al passaggio \#3, il risultato è lo stesso.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
