---
title: "ACSD-48661: problema di convalida del separatore virgola del limite di credito della società"
description: Applica la patch ACSD-48661 per risolvere il problema Adobe Commerce, in cui quando il limite di credito della società è superiore a 999, il separatore di virgola impedisce il salvataggio della società a causa di un errore di convalida.
exl-id: 85c5a93f-76c5-439b-adcc-511f8473f302
feature: Admin Workspace, B2B, Companies, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# ACSD-48661: problema di convalida del separatore virgola del limite di credito della società

La patch ACSD-48661 risolve il problema se, quando il limite di credito dell’azienda è maggiore di 999, il separatore di virgola impedisce il salvataggio dell’azienda a causa di un errore di convalida. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26. L’ID della patch è ACSD-48661. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.5-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando il limite di credito della società è superiore a 999, il separatore virgola impedisce il salvataggio della società a causa di un errore di convalida.

<u>Passaggi da riprodurre</u>:

1. Abilita la funzione aziendale in **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.
1. Crea una società e aggiungi un limite di credito maggiore di 999 nel **[!UICONTROL Company Credit]** scheda.
1. Salva la società.
1. Modifica l’azienda e prova a salvarla nuovamente.

<u>Risultati previsti</u>:

Puoi salvare la società senza fissare il limite di credito. La virgola non è supportata per i campi di input per gli importi e i prezzi.

<u>Risultati effettivi</u>:

Impossibile salvare la società a causa di un errore di convalida nella *[!UICONTROL Credit Limit]* campo. Adobe Commerce aggiunge automaticamente i separatori virgola per i limiti di credito anche se [!UICONTROL Credit Limit] Il campo non accetta virgole.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
