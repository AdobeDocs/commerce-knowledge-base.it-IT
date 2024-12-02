---
title: 'MDVA-41046: prodotti semplici con opzioni personalizzate non disponibili per l''assegnazione'
description: La patch MDVA-41046 risolve il problema, in cui non sono disponibili prodotti semplici con opzioni personalizzate da assegnare a un prodotto configurabile o raggruppato. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5. L'ID della patch è MDVA-41046. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
exl-id: 01229a69-c72a-4189-9be5-1761073b74ee
feature: Products
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-41046: prodotti semplici con opzioni personalizzate non disponibili per l&#39;assegnazione

La patch MDVA-41046 risolve il problema, in cui non sono disponibili prodotti semplici con opzioni personalizzate da assegnare a un prodotto configurabile o raggruppato. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5. L&#39;ID della patch è MDVA-41046. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Non sono disponibili prodotti semplici con opzioni personalizzate da assegnare a prodotti configurabili/raggruppati.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto semplice con opzioni personalizzabili e imposta un valore per l’attributo configurabile.
   * Utilizza *Colore* come attributo configurabile e seleziona *Giallo* come valore di colore.
1. Salva il prodotto semplice.
1. Ora vai alla pagina Crea prodotto configurabile.
1. Segui la procedura guidata &quot;Crea configurazione&quot; e assicurati di selezionare *Giallo* come colore dell&#39;attributo.
1. Senza salvare il prodotto configurabile, seleziona l’opzione &quot;Scegli un prodotto diverso&quot; dal menu a discesa Seleziona.
1. Verrà aperta una griglia di prodotto filtrata in base all’attributo di colore giallo. Ora seleziona il prodotto semplice creato in precedenza con opzioni personalizzabili.
1. Salva il prodotto configurabile.

<u>Risultati previsti</u>:

Il prodotto semplice con opzioni personalizzate è disponibile per l’assegnazione (visibile nella griglia) nel passaggio 6.

<u>Risultati effettivi</u>:

La sezione Configurazione è vuota.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
