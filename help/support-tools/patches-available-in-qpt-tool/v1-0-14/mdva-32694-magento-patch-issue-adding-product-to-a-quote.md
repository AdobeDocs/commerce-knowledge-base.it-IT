---
title: "Patch MDVA-32694: problema durante l'aggiunta di un prodotto a un preventivo"
description: La patch MDVA-32694 risolve il problema dell'impossibilità di aggiungere un prodotto valido in Admin a un preventivo negoziabile creato sul sito Web non predefinito.
exl-id: 964abbbd-c8b1-4645-a393-7283f52e94ff
feature: Products, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# Patch MDVA-32694: problema durante l&#39;aggiunta di un prodotto a un preventivo

La patch MDVA-32694 risolve il problema dell&#39;impossibilità di aggiungere un prodotto valido in Admin a un preventivo negoziabile creato sul sito Web non predefinito.

Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.14. Il problema è pianificato per la risoluzione in Adobe Commerce versione 2.4.3.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce su infrastruttura cloud 2.3.2 con versione 1.2 B2B

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce su infrastruttura cloud e Adobe Commerce on-premise 2.3.0 - 2.3.5-p2, 2.4.0, 2.4.1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Prerequisiti</u>:

Installa una nuova istanza di Adobe Commerce con B2B.

<u>Passaggi da riprodurre</u>:

1. Vai a **STORE > Configurazione > GENERALE > Funzioni B2B** e abilita **Azienda** e **Preventivo B2B**.
1. Crea altri 2 siti Web con **store** e **storiews** (In totale dovresti disporre di 3 siti web: *base*, *sito Web2*, *sito Web3*).
1. Creare un prodotto semplice e assegnarlo solo a *sito Web3*.
1. Vai a **STORE > Tutti i negozi** e imposta *sito Web3* as **predefinito**.
1. Vai al front-end e crea una nuova azienda in *sito Web3*.
1. Aggiungere al carrello il prodotto creato in precedenza e creare un nuovo preventivo negoziabile.
1. Vai a **STORE > Tutti i negozi** e imposta la &quot;*base*&quot; sito web torna come **predefinito**.
1. Vai a **VENDITE > Preventivi > Apri preventivo creato in precedenza** e provare ad aggiungervi lo stesso prodotto.

<u>Risultati previsti</u>:

L’utente amministratore può aggiungere all’offerta lo stesso prodotto, come previsto.

<u>Risultati effettivi</u>:

L’utente amministratore non può aggiungere lo stesso prodotto all’offerta e viene visualizzato il seguente messaggio di errore:

```php
This product is assigned to another website.
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
