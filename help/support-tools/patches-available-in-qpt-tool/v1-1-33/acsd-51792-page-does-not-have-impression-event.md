---
title: "ACSD-51792: la pagina non ha un evento di impression"
description: Applica la patch ACSD-51792 per risolvere il problema di prestazioni di Adobe Commerce, in cui una pagina non presenta l’evento di impression quando è abilitato Google Tag Manager 4.
exl-id: 59194d4c-c387-4372-a0ff-1cdd74f8c6df
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-51792: la pagina non ha un evento di impression

La patch ACSD-51792 risolve il problema di prestazioni, se una pagina non ha l’evento di impression, quando [!DNL Google Tag Manager] 4 è attivato. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.33. L’ID della patch è ACSD-51792. Il problema è stato risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La pagina non ha l’evento di impression quando [!DNL Google Tag Manager] 4 è attivato.

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]**.
1. Configurare **[!DNL GoogleTag Manager]** integrazione.
1. Vai a [Assistente tag Google](https://tagassistant.google.com/)e completare i passaggi necessari per connettersi al sito Web.
1. Apri una pagina di categoria con un elenco di prodotti nella vetrina.
1. Verifica la presenza dell’evento impression nell’osservatore di Tag Assistant.

<u>Risultati previsti</u>:

L’evento di impression deve iniziare con tutti i prodotti sulla pagina.

<u>Risultati effettivi</u>:

La pagina non presenta l’evento di impression nell’osservatore di Tag Assistant.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
