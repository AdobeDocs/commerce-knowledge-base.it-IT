---
title: "MDVA-37725: le e-mail inviate tramite siti non predefiniti contengono gli URL del logo del sito predefinito"
description: La patch MDVA-37725 risolve il problema dell'invio asincrono delle e-mail di ordine tramite siti Web non predefiniti contenenti gli URL del logo del sito Web predefinito.
exl-id: c0d1b9a3-01bb-445b-b7da-f9be6952eaeb
feature: Communications, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-37725: le e-mail inviate tramite siti non predefiniti contengono gli URL del logo del sito predefinito

>[!WARNING]
>
> La patch MDVA-37725 è obsoleta.

La patch MDVA-37725 risolve il problema dell&#39;invio asincrono delle e-mail di ordine tramite siti Web non predefiniti contenenti gli URL del logo del sito Web predefinito. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4. L&#39;ID della patch è MDVA-37725. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le e-mail di ordine asincrono vengono inviate tramite siti web non predefiniti contenenti gli URL del logo del sito web predefinito.

<u>Prerequisiti</u>:

1. Il secondo sito Web/store/store-view deve essere stato creato.
1. La configurazione **Invio asincrono** deve essere abilitata da **Archivi** > **Impostazioni** > **Configurazione** > **Vendite** > **E-mail vendite** > **Impostazioni generali**.
1. **L&#39;aggiunta del codice dello store alla configurazione degli URL** è attivata per facilitare l&#39;accesso al sito Web secondario da **Archivi** > **Impostazioni** > **Configurazione** > **Opzioni URL**.

<u>Passaggi da riprodurre</u>:

1. Effettuare ordini dal primo e dal secondo punto vendita.
1. Esegui cron per inviare le e-mail di vendita.
1. Controlla l’e-mail dal secondo sito web.

<u>Risultati previsti</u>:

L’URL del logo dell’e-mail contiene l’URL del secondo sito web.

<u>Risultati effettivi</u>:

L’URL del logo dell’e-mail contiene l’URL predefinito del sito web.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
