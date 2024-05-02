---
title: "ACSD-51528: diversi comportamenti nella formattazione snake_case"
description: Applica la patch ACSD-51528 per risolvere il problema Adobe Commerce, in presenza di comportamenti diversi nella formattazione di snake_case.
exl-id: dd878321-8032-41f3-8dcd-acb0cc023b44
feature: Variables
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# ACSD-51528: diversi comportamenti nella formattazione di snake_case

La patch ACSD-51528 corregge diversi comportamenti nella formattazione di snake_case. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.32. L’ID della patch è ACSD-51528. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I diversi comportamenti sulla formattazione snake_case.

<u>Passaggi da riprodurre</u>:

1. Testare `\Magento\Framework\Api\DataObjectHelper::populateWithArray` con una varietà di nomi di proprietà diversi.
1. Le proprietà con nomi come *NewPName* deve essere trasformato in *new_p_name*, invece vengono trasformati in *new_pname*.
1. Inoltre, quando si utilizza *getNewPName* funzione nell&#39;oggetto, *nulle* verrà restituito perché il *Modello astratto* trasformerà correttamente la chiamata a *new_p_name* rendendo entrambe le funzioni incompatibili tra loro.

<u>Risultati previsti</u>

Il **[!UICONTROL populateWithArray]** dovrebbe trasformare correttamente le proprietà dell’oggetto in snake_case, rendendolo compatibile con **[!DNL AbstractModel's]** `Getters` e `Setters`.

<u>Risultati effettivi</u>

Quando si utilizza **[!UICONTROL populateWithArray]** funzione, qualsiasi proprietà oggetto che contenga due o più lettere maiuscole in una riga nel nome causerà la trasformazione snake_case non corretta nell’array di dati finale.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
