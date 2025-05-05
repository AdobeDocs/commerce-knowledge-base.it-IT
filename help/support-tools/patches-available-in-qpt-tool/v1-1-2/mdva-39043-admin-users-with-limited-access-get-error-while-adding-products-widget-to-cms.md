---
title: 'MDVA-39043: errore restituito dagli utenti amministratori durante l''aggiunta del widget alla pagina CMS'
description: La patch MDVA-39043 risolve il problema che causava un errore agli utenti amministratori con accesso limitato durante l'aggiunta del widget "Prodotti" alla pagina CMS. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.2. L'ID della patch è MDVA-39043. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
exl-id: 63057351-e972-4575-9bf0-e818f590b40a
feature: Admin Workspace, CMS, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# MDVA-39043: errore restituito dagli utenti amministratori durante l&#39;aggiunta del widget alla pagina CMS

La patch MDVA-39043 risolve il problema che causava un errore agli utenti amministratori con accesso limitato durante l&#39;aggiunta del widget &quot;Prodotti&quot; alla pagina CMS. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.2. L&#39;ID della patch è MDVA-39043. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.4 - 2.4.3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli utenti amministratori con accesso limitato ricevono un errore durante l’aggiunta del widget &quot;Prodotti&quot; alla pagina CMS.

<u>Passaggi da riprodurre</u>:

1. Accedi al backend utilizzando l’amministratore con accesso solo per la modifica del contenuto.
1. Vai a **Contenuto** > **Pagine**.
1. Apri una pagina da modificare.
1. Modifica il contenuto con **Page Builder**.
1. Aggiungi il widget **Prodotto** dalla sezione **Aggiungi contenuto**.
1. Fai clic su **Configura** nel widget **Prodotto**.

<u>Risultati previsti</u>:

Non viene visualizzato alcun errore.

<u>Risultati effettivi</u>:

Viene ricevuto il seguente messaggio di errore:

`*A technical problem with the server created an error. Try again to continue what you were doing. If the problem persists, try again later.*`

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella documentazione per gli sviluppatori.
