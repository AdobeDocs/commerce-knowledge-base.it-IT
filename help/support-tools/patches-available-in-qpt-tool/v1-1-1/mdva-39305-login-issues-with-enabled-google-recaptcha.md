---
title: "MDVA-39305: problema di accesso con Google reCAPTCHA abilitato"
description: La patch MDVA-39305 risolve il problema che impediva ai clienti registrati di accedere con Google reCAPTCHA abilitato. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1. L'ID della patch è MDVA-39305. Il problema è pianificato per essere risolto nelle versioni 2.4.4 e 2.4.7 di Adobe Commerce.
exl-id: 1e8e7dc7-f8f1-4432-90f4-dc73d85f353a
feature: Console
role: Admin
source-git-commit: d48abbf3ecc19a78ee1d86a12d9c32cba17d53e5
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# MDVA-39305: problema di accesso con Google reCAPTCHA abilitato

La patch MDVA-39305 risolve il problema che impediva ai clienti registrati di accedere con Google reCAPTCHA abilitato. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1. L&#39;ID della patch è MDVA-39305. Il problema è pianificato per essere risolto nelle versioni 2.4.4 e 2.4.7 di Adobe Commerce.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce su infrastruttura cloud 2.4.2-p1, 2.4.3-p3, 2.4.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di distribuzione) 2.4.1-p1 - 2.4.3-p3, 2.4.4-p1 - 2.4.4-p5, 2.4.5 - 2.4.6-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I clienti registrati non sono in grado di effettuare l’accesso con Google reCAPTCHA abilitato.

<u>Passaggi da riprodurre</u>:

1. Vai a **Archivia** > **Configurazione** > **Sicurezza** > **Google reCAPTCHA Storefront** e abilita **Google reCAPTCHA**.
1. Vai a **Frontend**.
1. Apri **Console strumenti per sviluppatori** nel browser.

<u>Risultati previsti</u>:

Nessun avviso CSP nella console.

<u>Risultati effettivi</u>:

Avvisi CSP nella console.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
