---
title: "ACSD-50276: il modulo di registrazione cliente non funziona nella vetrina se viene creato un attributo cliente a selezione multipla"
description: Applica la patch ACSD-50276 per risolvere il problema di Adobe Commerce, a causa del quale il modulo di registrazione del cliente non funziona nella vetrina se viene creato un attributo cliente a selezione multipla.
exl-id: 542eb93a-3719-4e2d-bb1b-87817f0812b4
feature: Attributes, Storefront
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-50276: il modulo di registrazione cliente non funziona nella vetrina se viene creato un attributo cliente a selezione multipla

La patch ACSD-50276 risolve il problema che impedisce il funzionamento del modulo di registrazione del cliente nella vetrina se viene creato un attributo cliente a selezione multipla. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30. L’ID della patch è ACSD-50276. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il modulo di registrazione cliente non funziona nella vetrina se viene creato un attributo cliente a selezione multipla.

<u>Passaggi da riprodurre</u>:

1. Crea un nuovo attributo cliente a selezione multipla con le seguenti impostazioni:

   * *[!UICONTROL Required = Yes]*
   * *[!UICONTROL Show on storefront = Yes]*, seleziona *[!UICONTROL Customer registration form]*.

1. Apri il modulo di registrazione cliente nella vetrina.

<u>Risultati previsti</u>:

Il modulo di registrazione cliente viene caricato correttamente.

<u>Risultati effettivi</u>:

* Il modulo di registrazione cliente non viene caricato.
* Viene registrato il seguente errore:

  ```PHP
  report. CRITICAL: Exception: Deprecated Functionality: explode(): Passing null to parameter #2 ($string) of type string is deprecated in vendor/magento/module-custom-attribute-management/Block/Form/Renderer/Multiselect.php
  ```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
