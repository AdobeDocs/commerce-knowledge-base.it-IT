---
title: "MDVA-39966: impossibile distribuire impostazioni internazionali diverse da en_US"
description: La patch MDVA-39966 risolve il problema se l'utente non è in grado di distribuire impostazioni internazionali diverse da en_US. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2. L'ID della patch è MDVA-39966. Il problema è stato risolto nella versione 2.4.1 di Adobe Commerce.
exl-id: fc0f5ef4-f6be-4f0d-af8d-803b411510a9
feature: Deploy
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# MDVA-39966: impossibile distribuire impostazioni locali diverse da en_US

La patch MDVA-39966 risolve il problema se l&#39;utente non è in grado di distribuire impostazioni internazionali diverse da en_US. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2. L&#39;ID della patch è MDVA-39966. Il problema è stato risolto nella versione 2.4.1 di Adobe Commerce.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.3.5-p2, 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Impossibile distribuire impostazioni locali diverse da en_US.

<u>Passaggi da riprodurre</u>:

1. Configurate due viste store con impostazioni internazionali diverse, ad esempio en_US e de_DE.
1. Prova a distribuire il contenuto statico per queste impostazioni internazionali eseguendo il seguente comando:

```bash
bin/magento setup:static-content:deploy --language=en_US
bin/magento setup:static-content:deploy --language=de_DE
```

<u>Risultati previsti</u>:

de_DE locale è distribuito.

```bash
bin/magento setup:static-content:deploy --language=de_DE

Deploy using quick strategy
adminhtml/Magento/backend/de_DE         2416/2416           ============================ 100%   9 secs
frontend/Magento/blank/de_DE            2486/2486           ============================ 100%   7 secs
frontend/Magento/luma/de_DE             2504/2504           ============================ 100%   8 secs

Execution time: 27.062166929245
```

<u>Risultati effettivi</u>:

en_US locale distribuito invece di de_DE:

```bash
bin/magento setup:static-content:deploy --language=de_DE

Deploy using quick strategy
adminhtml/Magento/backend/en_US         2416/2416           ============================ 100%   2 secs
frontend/Magento/blank/en_US            2486/2486           ============================ 100%   1 sec
frontend/Magento/luma/en_US             2504/2504           ============================ 100%   2 secs
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
