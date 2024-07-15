---
title: "Patch MDVA-27664: errore dell'account della data di nascita"
description: La patch MDVA-27664 risolve il problema che la data di nascita di un account cliente potrebbe essere successiva alla data odierna.
exl-id: c669764e-b4a5-4031-92ac-1156755e9a0a
feature: Customer Service
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# Patch MDVA-27664: errore dell&#39;account della data di nascita

La patch MDVA-27664 risolve il problema che la data di nascita di un account cliente potrebbe essere successiva alla data odierna.

Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15. Il problema è stato risolto nella versione 2.3.6 di Adobe Commerce.

## Prodotti e versioni interessati

**La patch è stata creata per Adobe Commerce versione:** Adobe Commerce su infrastruttura cloud 2.3.4-p2

**Compatibile con le versioni di Adobe Commerce:** Adobe Commerce su infrastruttura cloud e Adobe Commerce on-premise 2.3.4 - 2.3.5-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Passaggi da riprodurre</u>:

1. Accedi all’amministratore.
1. Imposta **Locale** = *en\_GB* (Regno Unito) per un utente.
1. Modificare un cliente.
1. Selezionare una data di nascita dopo il 12 di un mese di quest&#39;anno.

<u>Risultati previsti</u>:

La data di nascita è valida, quindi le informazioni del cliente possono essere salvate come previsto.

<u>Risultati effettivi</u>:

Impossibile salvare le informazioni sul cliente perché si è verificato un errore di convalida:

```php
The Date of Birth should not be greater than today.
```

dove invece del formato data GG/MM/AAAA, la data è trattata come il formato data MM/GG/AAAA.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
