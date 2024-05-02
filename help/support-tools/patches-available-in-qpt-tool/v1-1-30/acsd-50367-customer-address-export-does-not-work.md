---
title: "ACSD-50367: l’esportazione dell’indirizzo del cliente non funziona con l’attributo a selezione multipla"
description: Applica la patch ACSD-50367 per risolvere il problema di Adobe Commerce per cui l’esportazione dell’indirizzo del cliente non funziona quando viene creato un attributo **`Indirizzo del cliente`** a selezione multipla senza valori.
exl-id: 688831d4-b49e-48fa-b4db-1328cda09a2b
feature: Admin Workspace, Attributes, Data Import/Export, Shipping/Delivery
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-50367: l’esportazione dell’indirizzo del cliente non funziona

La patch ACSD-50367 risolve il problema che impedisce il funzionamento dell&#39;esportazione dell&#39;indirizzo del cliente quando si effettua una selezione multipla **`Customer Address`** viene creato un attributo senza valori. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30. L’ID della patch è ACSD-50367. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’esportazione dell’indirizzo del cliente non funziona se è stata effettuata una selezione multipla **`Customer Address`** viene creato un attributo senza valori.

<u>Prerequisiti</u>:

Crea un cliente con un indirizzo.

<u>Passaggi da riprodurre</u>:

1. Creare una selezione multipla **`Customer Address`** attributo in **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Customer Addresses]**.
1. Vai a **[!UICONTROL Admin]** > **[!UICONTROL System]** > **[!UICONTROL Export]**, e seleziona **`Customer Address`** tipo di entità.
1. Esporta gli indirizzi dei clienti. Vedrai che non viene esportato nulla.
1. Elimina la selezione multipla **`Customer Address`** ed esportare di nuovo gli indirizzi dei clienti. Questa volta viene generato il file CSV degli indirizzi.

<u>Risultati previsti</u>:

Gli indirizzi dei clienti possono essere esportati come file CSV quando si effettua una selezione multipla **`Customer Address`** viene creato.

<u>Risultati effettivi</u>:

Gli indirizzi dei clienti non possono essere esportati come file CSV quando si effettua una selezione multipla **`Customer Address`** viene creato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
