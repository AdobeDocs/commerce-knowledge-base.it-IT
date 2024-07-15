---
title: "Patch MDVA-32012: convalida dei codici postali S. Korean e Argentina"
description: La patch MDVA-32012 risolve il problema relativo alla mancata convalida dei codici postali argentini e sudcoreani a causa di modifiche o variazioni nei formati dei codici postali nazionali. I codici postali sudcoreani devono ora essere a 5 cifre, mentre in precedenza erano a 6 cifre. I codici postali argentini possono essere sia numerici che alfanumerici. La patch MDVA-32012 indica che questi formati per i valori del codice postale verranno convalidati per questi paesi. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9. Il problema è pianificato per la risoluzione in Adobe Commerce versione 2.4.2.
exl-id: 9602f50d-6acd-4724-9734-6aeb65393a25
feature: Communications
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---

# Patch MDVA-32012: convalida dei codici postali di Corea del Sud e Argentina

La patch MDVA-32012 risolve il problema relativo alla mancata convalida dei codici postali argentini e sudcoreani a causa di modifiche o variazioni nei formati dei codici postali nazionali. I codici postali sudcoreani devono ora essere a 5 cifre, mentre in precedenza erano a 6 cifre. I codici postali argentini possono essere sia numerici che alfanumerici. La patch MDVA-32012 indica che questi formati per i valori del codice postale verranno convalidati per questi paesi. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9. Il problema è pianificato per la risoluzione in Adobe Commerce versione 2.4.2.

## Prodotti e versioni interessati

* La patch è stata progettata per Adobe Commerce sull’infrastruttura cloud 2.3.5.
* La patch è compatibile anche con le seguenti versioni di Adobe Commerce: Adobe Commerce su infrastruttura cloud e Adobe Commerce on-premise 2.3.0 - 2.4.1.

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’immissione di un codice postale sudcoreano a 5 cifre o argentino alfanumerico genera un’avvertenza:

*Il CAP fornito non è valido. Esempio: [1234 (se inserito un indirizzo alfanumerico argentino)] o [123-456 (se inserito un indirizzo sudcoreano di 5 cifre)]. Se ritieni che sia quello giusto, puoi ignorare questo avviso.*

<u>Passaggi da riprodurre</u>:

1. Apri la vetrina.
1. Aggiungi articolo al carrello.
1. Processo di estrazione.
1. Aggiungi un nuovo indirizzo con la Corea del Sud per il paese e inserisci un codice postale a 5 cifre oppure aggiungi un nuovo indirizzo con l’Argentina per il paese e inserisci un codice postale alfanumerico.
1. Prova a salvare.

<u>Risultati previsti</u>:

L’indirizzo deve essere salvato senza preavviso.

<u>Risultati effettivi</u>:

Il salvataggio dell&#39;indirizzo restituisce un avviso.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta le [patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
