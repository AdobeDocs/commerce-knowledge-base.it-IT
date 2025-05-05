---
title: 'ACSD-52041: il rendering di Page Builder non rilascia i blocchi'
description: Applica la patch ACSD-52041 per risolvere il problema di Adobe Commerce, in cui Page Builder esegue il rendering per cinque secondi senza rilasciare blocchi.
feature: Page Builder
role: Admin, Developer
exl-id: f2a1fd36-2098-46a7-aa42-3a5a0014adc9
source-git-commit: b5c253a5c0651c6027c0795edb2f230bd65f734a
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---

# ACSD-52041: il rendering di Page Builder non rilascia i blocchi

La patch ACSD-52041 risolve il problema relativo al rendering del Page Builder per cinque secondi senza rilasciare blocchi. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.48. L’ID della patch è ACSD-52041-v2. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.4-p5, 2.4.5 - 2.4.5-p4 e 2.4.6 - 2.4.6-p2.



>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.


## Problema

**[!DNL Page Builder]** esegue il rendering per *5* secondi senza rilasciare i blocchi.

<u>Passaggi da riprodurre</u>:

1. Modificare una pagina CMS, una pagina di prodotto o qualsiasi elemento con **[!DNL Page Builder]**.
1. Salva le modifiche.
1. Osserva il tempo di salvataggio della pagina.

<u>Risultati previsti</u>

Il contenuto viene salvato. Nessun errore trovato nel registro del browser.

<u>Risultati effettivi</u>

Il salvataggio richiede più tempo del solito.
Errore nella console: ``Page Builder was rendering for 5 seconds without releasing locks``

## Applicare la patch

Per applicare singole patch per le versioni **2.4.4 - 2.4.4-p5, 2.4.5 - 2.4.5-p4 e 2.4.6 - 2.4.6-p2**, utilizzare i collegamenti seguenti a seconda del metodo di distribuzione:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it>) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it>) nella guida di [!DNL Quality Patches Tool].
