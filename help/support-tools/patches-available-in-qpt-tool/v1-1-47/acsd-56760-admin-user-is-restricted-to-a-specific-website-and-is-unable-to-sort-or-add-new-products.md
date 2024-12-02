---
title: 'ACSD-56760: l’utente amministratore è limitato a un sito web specifico e non può ordinare o aggiungere nuovi prodotti'
description: Applica la patch ACSD-56760 per risolvere il problema di Adobe Commerce, a causa del quale l’utente amministratore limitato a un sito web specifico e non è in grado di ordinare o aggiungere nuovi prodotti all’interno di una categoria nel caso in cui lo store web abbia la propria categoria principale.
role: Admin
exl-id: fc1898ce-dcd7-4c0b-bef0-445219e8455f
source-git-commit: a8e1b3b5b9de41c62bf819ef68ac9f89626483a1
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---

# ACSD-56760: l’utente amministratore è limitato a un sito web specifico e non può ordinare o aggiungere nuovi prodotti

La patch ACSD-56760 risolve il problema per cui l’utente amministratore, limitato a un sito web specifico e impossibilitato a ordinare o aggiungere nuovi prodotti all’interno di una categoria, nel caso in cui il web store abbia la propria categoria principale. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.47. L’ID della patch è ACSD-56760. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’utente amministratore limitato a un sito web specifico e che non è in grado di ordinare o aggiungere nuovi prodotti all’interno di una categoria nel caso in cui il web store abbia la propria categoria principale.

<u>Passaggi da riprodurre</u>:

1. Creare *2* siti Web.
1. Crea un **[!UICONTROL restricted admin user]** con accesso solo al sito Web *1*.
1. Accedi come **[!UICONTROL restricted admin user]** e prova a modificare le posizioni del prodotto in una categoria.

*Caso 1*:

* *2* archivi.
* *2* categorie principali, ogni sito Web assegnato alla propria categoria principale.

*Caso 2*:

* *2* archivi.
* Solo la categoria principale *1* è assegnata a entrambi i siti Web.

<u>Risultati previsti</u>:

* *Caso 1*: l&#39;amministratore con restrizioni deve essere in grado di ordinare i prodotti all&#39;interno della categoria disponibile.
* *Caso 2*: l&#39;amministratore con restrizioni non può ordinare i prodotti all&#39;interno della categoria disponibile, perché questo influirà anche sull&#39;archivio con restrizioni.

<u>Risultati effettivi</u>:

* *Caso 1*: l&#39;amministratore con restrizioni non è in grado di ordinare i prodotti all&#39;interno della categoria disponibile.
* *Caso 2*: l&#39;amministratore con restrizioni può ordinare i prodotti all&#39;interno della categoria disponibile, influenzando gli archivi con restrizioni.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
