---
title: "ACSD-52041: il rendering di Page Builder non rilascia i blocchi"
description: Applica la patch ACSD-52041 per risolvere il problema di Adobe Commerce, in cui Page Builder esegue il rendering per cinque secondi senza rilasciare blocchi.
feature: Page Builder
role: Admin, Developer
exl-id: f2a1fd36-2098-46a7-aa42-3a5a0014adc9
source-git-commit: fc5dc9fcf610cae6f8c0a334b4ef15029c462c66
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# ACSD-52041: il rendering di Page Builder non rilascia i blocchi

La patch ACSD-52041 risolve il problema relativo al rendering del Page Builder per cinque secondi senza rilasciare blocchi. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.48. L’ID della patch è ACSD-52041-v2. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.4-p8, 2.4.5 - 2.4.5-p7, 2.4.6 - 2.4.6-p6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il Page Builder esegue il rendering per cinque secondi senza rilasciare blocchi.

<u>Passaggi da riprodurre</u>:

1. Modificare una pagina CMS, una pagina di prodotto o qualsiasi altro elemento con Page Builder.
1. Salva le modifiche.
1. Osserva il tempo di salvataggio della pagina.

<u>Risultati previsti</u>

Il contenuto viene salvato. Nessun errore trovato nel registro del browser.

<u>Risultati effettivi</u>

Il salvataggio richiede più tempo del solito.
Errore nella console: ``Page Builder was rendering for 5 seconds without releasing locks``

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) nel [!DNL Quality Patches Tool] guida.
