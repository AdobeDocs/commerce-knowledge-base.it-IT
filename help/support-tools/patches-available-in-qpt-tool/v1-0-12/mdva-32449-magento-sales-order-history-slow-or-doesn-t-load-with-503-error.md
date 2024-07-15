---
title: "MDVA-32449: cronologia ordini cliente lenta o non caricata con errore 503"
description: La patch MDVA-32449 risolve il problema relativo ad Adobe Commerce, in cui la cronologia degli ordini di vendita viene caricata lentamente o non viene caricata e viene visualizzato un errore 503. Si tratta di un problema che si verifica quando i clienti 13000+ vengono assegnati a un’azienda B2B. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12. Questo problema è stato risolto in Adobe Commerce 2.4.1.
exl-id: e3fd4db2-b706-4712-ba8e-270eaca7fdb2
feature: B2B, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# MDVA-32449: cronologia ordini cliente lenta o non caricata con errore 503

La patch MDVA-32449 risolve il problema relativo ad Adobe Commerce, in cui la cronologia degli ordini di vendita viene caricata lentamente o non viene caricata e viene visualizzato un errore 503. Si tratta di un problema che si verifica quando i clienti 13000+ vengono assegnati a un’azienda B2B. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12. Questo problema è stato risolto in Adobe Commerce 2.4.1.

## Prodotti e versioni interessati

Si tratta di un problema che si verifica quando i clienti 13000+ vengono assegnati a un’azienda B2B.

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.4.1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce su infrastruttura cloud e Adobe Commerce on-premise 2.3.0 - 2.3.5-p2, 2.4.0, 2.4.1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

È stato risolto il problema che causava il caricamento molto lento o nullo della cronologia degli ordini.

<u>Prerequisiti</u>:

13000+ clienti assegnati a un’azienda B2B

<u>Passaggi da riprodurre</u>:

1. Accedi alla vetrina come amministratore della società.
1. Passare alla pagina Cronologia ordini cliente.

<u>Risultati previsti</u>:

La pagina Storico ordini cliente viene caricata normalmente.

<u>Risultati effettivi</u>:

La pagina viene caricata molto lentamente o la pagina potrebbe non venire caricata e viene visualizzato un errore di timeout.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta le [patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
