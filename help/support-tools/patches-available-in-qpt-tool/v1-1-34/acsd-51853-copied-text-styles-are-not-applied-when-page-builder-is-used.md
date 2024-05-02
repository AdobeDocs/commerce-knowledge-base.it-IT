---
title: "ACSD-51853: gli stili di testo copiati non vengono applicati utilizzando il generatore di pagine"
description: Applica la patch ACSD-51853 per risolvere il problema di Adobe Commerce, per cui gli stili di testo copiati non vengono applicati quando si utilizza il generatore di pagine.
feature: Page Builder
role: Admin
exl-id: 1efd3147-1ae0-468b-af04-1632fbaaefda
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# ACSD-51853: gli stili di testo copiati non vengono applicati utilizzando il generatore di pagine

La patch ACSD-51853 risolve il problema per cui gli stili di testo copiati non vengono applicati quando si utilizza Page Builder. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.34. L’ID della patch è ACSD-51853. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli stili di testo copiati non vengono applicati quando si utilizza Page Builder

<u>Passaggi da riprodurre</u>:

1. Accedi ad Admin.
1. Vai a > **contenuto** > **pagine** > **Apri qualsiasi pagina** > **Modifica con Page Builder**.
1. Trascina riga e *Testo* da **[!UICONTROL Elements]**.
1. Copia **contenuto arricchito**, incolla il testo in una **[!UICONTROL Page Builder]**.

<u>Risultati previsti</u>

Il testo copiato viene incollato con tutti gli stili.

<u>Risultati effettivi</u>

Il testo copiato viene incollato come testo normale e tutti gli stili vengono persi.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
