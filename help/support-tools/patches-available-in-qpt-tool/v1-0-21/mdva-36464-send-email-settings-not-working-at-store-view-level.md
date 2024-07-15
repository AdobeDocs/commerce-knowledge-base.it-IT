---
title: "MDVA-36464: le impostazioni di invio e-mail non funzionano a livello di visualizzazione archivio"
description: La patch MDVA-36464 risolve il problema che impedisce il funzionamento delle impostazioni di invio e-mail a livello di visualizzazione store. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21. L'ID della patch è MDVA-36464. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.3.
exl-id: cdf7e208-90ee-4711-8407-026da42fe3c8
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# MDVA-36464: le impostazioni di invio e-mail non funzionano a livello di visualizzazione archivio

La patch MDVA-36464 risolve il problema che impedisce il funzionamento delle impostazioni di invio e-mail a livello di visualizzazione store. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21. L&#39;ID della patch è MDVA-36464. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.4.0-p1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Prerequisito:</u>

Installa clean Adobe Commerce.

<u>Passaggi da riprodurre</u>:

1. Creare una visualizzazione aggiuntiva del sito Web, dello store e dello store (in questo esempio, il secondo sito Web è *sito Web2*).
1. Disabilita **Notifica e-mail** a livello globale in **Store** > **Config** > **Advanced** > **System** > **Impostazioni invio posta**.
1. Abilita **Notifica e-mail** nel livello *sito Web2* (**Disabilita comunicazioni e-mail** = *No*).
1. In Amministratore, creare un nuovo utente e assegnarlo al *sito Web2*.
1. In Amministratore, nella pagina di modifica del cliente, fai clic su **Reimposta password** per il cliente creato in precedenza nel passaggio 4.

<u>Risultati previsti</u>:

Sia l&#39;e-mail di benvenuto di **** che l&#39;e-mail di reimpostazione della password **vengono inviate, come previsto, perché** Disabilita comunicazioni e-mail **= *No* per il secondo sito Web (esempio: *sito Web2*).**

<u>Risultati effettivi</u>:

* L&#39;**e-mail di benvenuto** dopo la creazione del nuovo cliente non viene attivata.
* L&#39;e-mail di reimpostazione password **** non è attivata.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
