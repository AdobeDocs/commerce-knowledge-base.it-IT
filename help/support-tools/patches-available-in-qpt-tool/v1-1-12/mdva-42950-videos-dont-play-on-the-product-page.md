---
title: 'MDVA-42950: i video non vengono riprodotti nella pagina del prodotto'
description: La patch MDVA-42950 risolve il problema relativo alla mancata riproduzione di video nella pagina del prodotto. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12. L'ID della patch è MDVA-42950. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: e19e5ff0-9ddd-41de-b64b-4c3aef4d16a5
feature: Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# MDVA-42950: i video non vengono riprodotti nella pagina del prodotto

La patch MDVA-42950 risolve il problema relativo alla mancata riproduzione di video nella pagina del prodotto. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12. L&#39;ID della patch è MDVA-42950. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I video non vengono riprodotti sulla pagina del prodotto.

<u>Passaggi da riprodurre</u>:

1. Configura la chiave API di YouTube passando a **Archivi** > **Configurazione** > **Catalogo** > **Video prodotto**.
1. Aggiungi un video da YouTube a un prodotto semplice con un elemento padre configurabile.
1. Aggiungi HEADER HTML nel contenuto > **Progettazione** > **Configurazione** > **Intestazione HTML** > **Script e fogli di stile**:

   ```HTML
   <script async="" src="https://www.youtube.com/iframe_api"></script>`
   ```

1. Vai al PDP e seleziona la configurazione del prodotto per visualizzare il video nell’elenco delle foto e dei video.
1. Prova a riprodurre il video.

<u>Risultati previsti</u>:

Riproduzione del video in corso.

<u>Risultati effettivi</u>:

Il video non viene riprodotto.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella documentazione per gli sviluppatori.
