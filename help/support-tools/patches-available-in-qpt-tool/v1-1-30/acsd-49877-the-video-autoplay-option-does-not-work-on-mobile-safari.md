---
title: '"ACSD-49877: la riproduzione automatica video non funziona sui dispositivi mobili [!DNL Safari]'''
description: Applica la patch ACSD-49877 per risolvere il problema di Adobe Commerce, se l’opzione di riproduzione automatica video non funziona su dispositivi mobili [!DNL Safari] quando il video è collegato direttamente a un file video remoto.
exl-id: 454f7cec-29b9-485b-93be-2a4f2eb77da7
feature: CMS
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# ACSD-49877: la riproduzione automatica video non funziona sui dispositivi mobili [!DNL Safari]

L&#39;ACSD-49877 risolve il problema in cui l&#39;opzione di riproduzione automatica su dispositivi mobili [!DNL Safari] non funziona quando il video è collegato direttamente a un file video remoto. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30. L’ID della patch è ACSD-49877. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la [!magento/quality-patches] alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: cerca le patch]. Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La riproduzione automatica video non funziona sui dispositivi mobili [!DNL Safari] quando il video è collegato direttamente a un file video remoto e non a un servizio di streaming.

<u>Prerequisiti</u>:
[!DNL Page Builder] sono installati.

<u>Passaggi da riprodurre</u>:

1. Crea una nuova pagina CMS e modifica il **[!UICONTROL Content Value]** con [!DNL Page Builder].
1. Aggiungi un *Linguetta* al contenuto e aggiungi un *Elemento video* all&#39;interno del *Linguetta*.
1. Ora fai clic sul pulsante con l’ingranaggio per modificare *Elemento video*.
1. Aggiungere un collegamento a un file video mp4 in [!UICONTROL Video URL] campo.
1. Contrassegna **[!UICONTROL Autoplay]** campo come *Sì*.
1. Clic **[!UICONTROL Save]**.
1. Apri la pagina creata di recente il [!DNL Safari] utilizzando un’iPhone.

<u>Risultati previsti</u>

L’opzione Riproduzione automatica funziona su [!DNL Safari] utilizzando un’iPhone.

<u>Risultati effettivi</u>

L’opzione Riproduzione automatica non funziona su [!DNL Safari] utilizzando un’iPhone.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
