---
title: "MDVA-29148: ArrayBackend non assegna il valore predefinito al salvataggio"
description: La patch MDVA-29148 risolve il problema per cui "\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend" non assegna il valore predefinito al salvataggio. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7. Il problema è stato risolto in Adobe Commerce 2.4.2.
exl-id: 7b2f5c18-0e7a-485b-a07e-700e435697fd
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-29148: ArrayBackend non assegna il valore predefinito al salvataggio

La patch MDVA-29148 risolve il problema per cui `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` non assegna il valore predefinito al momento del salvataggio. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7. Il problema è stato risolto in Adobe Commerce 2.4.2.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce su infrastruttura cloud 2.3.3-p1.

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) >=2.3.0 &lt;2.4.2.

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando un prodotto viene creato tramite uno script di importazione o l&#39;API REST, agli attributi che utilizzano il modello backend `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` e dispongono di un valore predefinito non viene assegnato il valore predefinito.

<u>Passaggi da riprodurre</u>:

1. Creare un nuovo attributo globale che utilizza il modello di back-end `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` e un valore predefinito non vuoto.
1. Utilizza l’API REST per creare un nuovo prodotto.
1. Recupera il nuovo prodotto dall’API REST e conferma che l’attributo non sia presente negli attributi personalizzati del prodotto.

<u>Risultati previsti</u>:

Il valore predefinito dell’attributo personalizzato è stato salvato nell’attributo del prodotto.

<u>Risultati effettivi</u>:

Il valore predefinito dell’attributo personalizzato non è stato salvato nell’attributo del prodotto.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
