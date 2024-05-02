---
title: "ACSD-51291: l’amministratore con restrizioni può aggiungere immagini/video a prodotti assegnati a più siti web"
description: Applica la patch ACSD-51291 per risolvere il problema di Adobe Commerce, in cui un amministratore con restrizioni di accesso a un sito web può aggiungere immagini/video a un prodotto assegnato a più siti web.
feature: Admin Workspace, Products, Page Content
role: Admin
exl-id: d3cf5009-6b80-4841-95c3-75bb15c9c0a4
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---

# ACSD-51291: l’amministratore con restrizioni può aggiungere immagini/video a prodotti assegnati a più siti web

La patch ACSD-51291 risolve il problema per cui un amministratore con restrizioni con accesso a un sito web può aggiungere immagini/video a un prodotto assegnato a più siti web. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.32. L’ID della patch è ACSD-51291. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.4-p3, 2.4.5 - 2.4.5-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Un amministratore con restrizioni di accesso a un sito web può aggiungere immagini/video a un prodotto assegnato a più siti web.

<u>Passaggi da riprodurre</u>

1. Accedi come amministratore.
1. Crea un secondo sito Web, store e visualizzazione store.
1. Crea un secondo ruolo di amministratore con risorse solo per il secondo sito Web, store e visualizzazione store.
1. Crea un secondo amministratore e assegnalo al nuovo ruolo di amministratore con restrizioni.
1. Crea un nuovo prodotto e assegnalo ai siti Web predefiniti e nuovi.
1. Esci dal profilo di amministrazione principale.
1. Accedi come nuovo amministratore con restrizioni.
1. Modifica il prodotto creato, che è stato assegnato a entrambi i siti web.
1. Apri **[!UICONTROL Images and Videos]** scheda.

<u>Risultati previsti</u>:

* Viene visualizzato il seguente messaggio:

  *L’amministratore con restrizioni può eseguire azioni su immagini o video solo quando dispone dei diritti per tutti i siti web a cui è assegnato il prodotto.*

* Il **[!UICONTROL Add Video]** non è attivo.

<u>Risultati effettivi</u>:

L’amministratore con restrizioni può aggiungere immagini e video anche quando il prodotto viene assegnato a un sito web a cui non ha accesso.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
