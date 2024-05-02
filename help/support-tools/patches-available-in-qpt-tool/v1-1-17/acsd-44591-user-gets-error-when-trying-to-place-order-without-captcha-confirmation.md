---
title: "ACSD-44591: errori durante l’ordine senza conferma CAPTCHA"
description: La patch ACSD-44591 risolve il problema relativo agli errori che si verificano quando si tenta di effettuare un ordine senza conferma CAPTCHA.
exl-id: 5459aa14-dcba-474d-aafa-e4cc73daafbc
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-44591: errori durante l’ordine senza conferma CAPTCHA

La patch ACSD-44591 risolve il problema relativo agli errori che si verificano quando si tenta di effettuare un ordine senza conferma CAPTCHA.
Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17. L’ID della patch è ACSD-44591. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’utente riceve errori quando tenta di effettuare un ordine senza conferma CAPTCHA.

<u>Passaggi da riprodurre</u>:

1. Configura Google ReCaptcha v2 (non sono un robot).
1. Abilita ReCaptcha per l’estrazione.
1. Provare a effettuare un ordine senza fare clic sul ReCaptcha.
1. Quando ricevi il messaggio di errore per ReCaptcha mancante (*Convalida ReCaptcha non riuscita, riprova*), fai clic su **ReCaptcha** e prova a fare un ordine.

<u>Risultati previsti</u>:

L’ordine non verrà effettuato con ReCaptcha errato.

<u>Risultati effettivi</u>:

Vengono visualizzati i seguenti errori:

* *Convalida ReCaptcha non riuscita, riprova*
* *Nessun carrello con ID = 1*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
