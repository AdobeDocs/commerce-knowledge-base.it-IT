---
title: '"ACSD-55305: Blocco dei popup durante la modifica dell’utente aziendale in [!UICONTROL My Account]'''
description: Applicare la patch ACSD-55305 per risolvere il problema Adobe Commerce in cui [!UICONTROL Edit Company User] popup sul [!UICONTROL My Account] &gt; [!UICONTROL Company Structure] La pagina si blocca con un caricatore sullo schermo.
feature: Companies, B2B
role: Admin, Developer
exl-id: be2bfe08-d05e-485d-84c3-2ff14e1a8654
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-55305: blocco dei popup durante la modifica dell’utente aziendale in [!UICONTROL My Account]

La patch ACSD-55305 risolve il problema dove  [!UICONTROL Edit Company User] popup sul [!UICONTROL My Account]> [!UICONTROL Company Structure] La pagina si blocca con un caricatore sullo schermo. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43. L’ID della patch è ACSD-55305. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Si verifica un errore durante il tentativo di utilizzo di *[!UICONTROL Edit Company User]* popup sul *[!UICONTROL My Account]* > *[!UICONTROL Company Structure]* , quando si blocca con un caricatore visualizzato sullo schermo.

<u>Passaggi da riprodurre</u>:

1. Creare un’azienda B2B.
1. Crea un attributo a selezione multipla per i clienti.
1. Assegna un valore all’attributo appena creato per l’amministratore della società.
1. Accedi come amministratore della società.
1. Vai a [!UICONTROL account dashboard] e passare alla **[!UICONTROL Company Structure]**.
1. Seleziona l’utente.
1. Fai clic su **[!UICONTROL Edit Selected]**.

<u>Risultati previsti</u>:

La finestra a comparsa del modulo viene visualizzata con precisione, offrendo la possibilità di modificare le informazioni aziendali.

<u>Risultati effettivi</u>:

Il menu a comparsa del modulo viene visualizzato senza alcuna possibilità di modifica.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
