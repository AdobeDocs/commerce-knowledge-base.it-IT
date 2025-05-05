---
title: "MDVA-38346: i filtri data non funzionano quando il fuso orario di Adobe Commerce è diverso da quello locale"
description: La patch MDVA-38346 risolve il problema relativo al malfunzionamento dei filtri di data quando il fuso orario di Adobe Commerce è diverso da quello dell’ambiente locale. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9. L'ID della patch è MDVA-38346. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
exl-id: 221ac249-add3-46e9-b0da-688eacdb753e
feature: Configuration
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-38346: i filtri data non funzionano quando il fuso orario di Adobe Commerce è diverso da quello locale

La patch MDVA-38346 risolve il problema relativo al malfunzionamento dei filtri di data quando il fuso orario di Adobe Commerce è diverso da quello dell’ambiente locale. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9. L&#39;ID della patch è MDVA-38346. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1, 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I filtri di data non funzionano correttamente se il fuso orario di Adobe Commerce è diverso da quello dell’ambiente locale.

<u>Passaggi da riprodurre</u>:

1. Cambia il fuso orario in Australia/Sydney.
1. Effettuare pochi ordini.
1. Creare le relative fatture.
1. Vai a **Vendite** > **Fatture** e filtra per Data fattura (data corrente - data corrente).
1. Controlla le date.

<u>Risultati previsti</u>:

La data della fattura visualizzata e il filtro effettivo corrispondono.

<u>Risultati effettivi</u>:

La data della fattura visualizzata è anteriore di un giorno rispetto al filtro effettivo (data corrente + 1 giorno).

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella documentazione per gli sviluppatori.
