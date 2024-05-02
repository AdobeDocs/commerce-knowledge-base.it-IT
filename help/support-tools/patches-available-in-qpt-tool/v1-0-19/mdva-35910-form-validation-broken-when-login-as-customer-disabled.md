---
title: 'MDVA-35910: convalida del modulo interrotta quando "Accedi come cliente" è disabilitato'
description: La patch MDVA-35910 risolve il problema relativo all'interruzione della convalida del modulo Crea account cliente quando l'estensione **Accedi come cliente** è disabilitata. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19. L'ID della patch è MDVA-35910. Il problema è stato risolto nella versione 2.4.3 di Adobe Commerce.
exl-id: fa63d725-33f0-4422-bcd5-d62dfee01b65
feature: Cache
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-35910: convalida del modulo interrotta quando &quot;Accedi come cliente&quot; è disabilitato

La patch di MDVA-35910 risolve il problema relativo all&#39;interruzione della convalida del modulo Crea account cliente quando **Accedi come cliente** l&#39;estensione è disabilitata. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19. L&#39;ID della patch è MDVA-35910. Il problema è stato risolto nella versione 2.4.3 di Adobe Commerce.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.4.1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.1-2.4.2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Passaggi da riprodurre</u>:

1. Accedi a **Archivi > Configurazione > Clienti**. Disattiva **Accedi come cliente** in Admin.
1. Sotto **Accedi come cliente**, impostato **Abilita estensione** = *No*.
1. Salva la configurazione e svuota la cache.
1. Torna alla vetrina e fai clic su **Registrati** (Crea un account cliente).
1. Compila il modulo dell’account e conferma se la convalida in **Conferma e-mail** funziona o meno.

<u>Risultati previsti</u>:

Il processo di creazione dell&#39;account cliente viene completato senza errori.

<u>Risultati effettivi</u>:

Il processo di creazione dell’account cliente non è completo e vengono invece visualizzati gli errori della console JavaScript.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
