---
title: 'MDVA-41628: gli utenti amministratori con restrizioni hanno accesso a nuove risorse'
description: La patch MDVA-41628 risolve il problema che consente agli utenti amministratori con restrizioni di accedere alle nuove risorse quando vengono aggiunti nuovi moduli. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12. L'ID della patch è MDVA-41628. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: 8f63ce9d-07b6-4d9d-a51b-b85b783b2adf
feature: Admin Workspace
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# MDVA-41628: gli utenti amministratori con restrizioni hanno accesso a nuove risorse

La patch MDVA-41628 risolve il problema che consente agli utenti amministratori con restrizioni di accedere alle nuove risorse quando vengono aggiunti nuovi moduli. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12. L&#39;ID della patch è MDVA-41628. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli utenti amministratori con restrizioni possono accedere alle nuove risorse quando vengono aggiunti nuovi moduli.

<u>Passaggi da riprodurre</u>:

1. Crea un nuovo ruolo utente amministratore con risorse limitate.
1. Crea un nuovo utente amministratore sotto il ruolo creato nel passaggio 1.
1. Installa e abilita il modulo personalizzato che crea un nuovo set di voci di menu insieme alle risorse ACL.
1. Accedi utilizzando il nuovo utente amministratore creato.

<u>Risultati previsti</u>:

L’utente amministratore con accesso limitato non può accedere alle nuove voci di menu create.

<u>Risultati effettivi</u>:

L’utente amministratore con restrizioni può accedere alle nuove voci di menu, anche se le nuove risorse non sono assegnate al ruolo utente.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella documentazione per gli sviluppatori.
