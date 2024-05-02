---
title: "MDVA-32632: Ordini nei sistemi di pagamento ma non in Adobe Commerce"
description: MDVA-32632 risolve il problema degli ordini in un sistema di pagamento ma non in Adobe Commerce. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12. Il problema è stato risolto in Adobe Commerce 2.3.5.
exl-id: f9b2fee4-9905-47cb-a71a-121426e93beb
feature: Orders, Payments, System
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# MDVA-32632: Ordini nei sistemi di pagamento ma non in Adobe Commerce

MDVA-32632 risolve il problema degli ordini in un sistema di pagamento ma non in Adobe Commerce. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12. Il problema è stato risolto in Adobe Commerce 2.3.5.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.2-p2

**La patch è compatibile anche con la versione Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud e Adobe Commerce on-premise 2.3.2 - 2.3.4-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il pagamento viene elaborato in un sistema di pagamento, ma l’ordine non viene creato in Adobe Commerce.

<u>Passaggi da riprodurre</u>:

1. Effettuare un ordine utilizzando un metodo di pagamento online.
1. Controlla l’ordine nell’amministratore di Commerce.

<u>Risultati previsti</u>:

Gli ordini completati vengono ora visualizzati nel sistema di pagamento e in Adobe Commerce.

<u>Risultati effettivi</u>:

Gli ordini sono stati elaborati correttamente dal sistema di pagamento ma non in Adobe Commerce.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
