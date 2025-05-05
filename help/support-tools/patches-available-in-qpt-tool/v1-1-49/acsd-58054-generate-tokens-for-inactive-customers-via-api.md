---
title: 'ACSD-58054: generazione di token API per clienti inattivi'
description: Applica la patch ACSD-58054 per risolvere il problema di Adobe Commerce, dove è possibile generare token cliente per i clienti inattivi tramite API.
feature: Customers, API Mesh
role: Admin, Developer
exl-id: 8c95ff8e-94b1-453a-9bb8-388612b6408f
source-git-commit: 06f751e43ef825c0eb29cb9b42eb41f07c308625
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# ACSD-58054: generazione di token API per clienti inattivi

La patch ACSD-58054 risolve il problema quando è possibile generare token cliente per i clienti inattivi tramite API. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49. L’ID della patch è ACSD-58054. Il problema è pianificato per essere risolto in B2B 1.5.1.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.5-p9

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Generazione di token cliente inattivi tramite API.

<u>Prerequisiti</u>:

Vengono installati i moduli B2B.

<u>Passaggi da riprodurre</u>:

1. Crea un account cliente.
1. Crea un token cliente utilizzando l’API.
1. Passa al backend e disabilita l’account del cliente.
1. Prova a generare di nuovo un token cliente.

<u>Risultati previsti</u>:

Token non generato.

<u>Risultati effettivi</u>:

Viene generato un token.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
