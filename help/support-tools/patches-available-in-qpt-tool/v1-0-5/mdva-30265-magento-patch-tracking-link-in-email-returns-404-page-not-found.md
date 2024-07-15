---
title: "MDVA-30265: il collegamento di tracciamento nell’e-mail restituisce una pagina 404 non trovata"
description: La patch MDVA-30265 risolve il problema dell'errore "404 Page not Found" quando il cliente fa clic sul collegamento di tracciamento della spedizione nell'e-mail di conferma dell'ordine. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5. Il problema è stato risolto in Adobe Commerce 2.4.2.
exl-id: 53e1ca98-dfa0-445b-a71a-56fd01b630ec
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---

# MDVA-30265: il collegamento di tracciamento nell&#39;e-mail restituisce la pagina 404 non trovata

La patch MDVA-30265 risolve il problema dell&#39;errore &quot;404 Page not Found&quot; quando il cliente fa clic sul collegamento di tracciamento della spedizione nell&#39;e-mail di conferma dell&#39;ordine. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5. Il problema è stato risolto in Adobe Commerce 2.4.2.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) da 2.3.3 a 2.4.1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Dopo aver creato la spedizione per un ordine effettuato, viene inviata al cliente un’e-mail con le informazioni di tracciamento e un collegamento per tenere traccia dell’ordine. Tuttavia, quando il cliente fa clic sul collegamento di tracciamento della spedizione nell’e-mail, viene restituito un errore &quot;404 Page not Found&quot; (Pagina 404 non trovata).

<u>Passaggi da riprodurre</u>:

1. Installare Adobe Commerce 2.4. Per i passaggi, consulta [Installare Adobe Commerce utilizzando Composer](https://devdocs.magento.com/guides/v2.4/install-gde/composer.html) nella documentazione per gli sviluppatori.
1. Effettua un ordine.
1. Vai al pannello di amministrazione > **Vendite** > **Ordini**. Cerca l’ordine appena creato e aprilo.
1. Crea una spedizione e aggiungi un numero di registrazione (vettore = valore personalizzato). Per i passaggi, consulta [Order Management > Creazione di una spedizione](https://docs.magento.com/user-guide/sales/shipments-create.html) nella nostra guida utente.
1. Ricevi un’e-mail. Fai clic sul collegamento di tracciamento per verificare se funziona.
1. Creare una fattura. Per i passaggi, consulta [Order Management > Creazione di una fattura](https://docs.magento.com/user-guide/sales/invoice-create.html) nella guida utente. Quindi fai di nuovo clic sul collegamento di tracciamento qui sopra.

<u>Risultati previsti</u>:

Il collegamento di verifica dovrebbe funzionare anche dopo la creazione della fattura.

<u>Risultati effettivi</u>:

Dopo aver creato la fattura, il collegamento di verifica non funziona e restituisce una pagina di errore &quot;404 Pagina non trovata&quot;.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
