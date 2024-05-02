---
title: '"ACSD-53204: *Errore "Impossibile salvare il prodotto*" su richieste simultanee di aggiunta di immagini alla raccolta"'
description: Applica la patch ACSD-53204 per risolvere il problema di Adobe Commerce, se viene generato l’errore *The product can not be save* (Impossibile salvare il prodotto) quando si eseguono richieste simultanee per aggiungere immagini alla galleria di prodotti utilizzando l’endpoint rest/V1/products/&lt;sku&gt;/media.
feature: Catalog Management, Media, Products, REST
role: Admin, Developer
exl-id: dcea2621-66cf-49d1-bba6-b61c70716e84
source-git-commit: e1ab32a4540ea7483f7f2b8464ef3e4b0ecbbac7
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-53204: &quot;*Impossibile salvare il prodotto*&quot;errore nelle richieste simultanee di aggiunta di immagini alla raccolta

La patch ACSD-53204 risolve il problema in cui &quot;*Impossibile salvare il prodotto*&quot;viene generato un errore quando si eseguono richieste simultanee per aggiungere immagini alla galleria di prodotti utilizzando `rest/V1/products/<sku>/media` endpoint. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.39. L’ID della patch è ACSD-53204. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

&quot;*Impossibile salvare il prodotto*&quot;viene generato un errore quando si eseguono richieste simultanee per aggiungere immagini alla galleria di prodotti utilizzando `rest/V1/products/<sku>/media` endpoint.

<u>Passaggi da riprodurre</u>:

1. Accedi al pannello di amministrazione.
1. Crea un prodotto con SKU p1.
1. Effettuare più richieste simultanee al `rest/V1/products/<sku>/media` per caricare più immagini contemporaneamente.

<u>Risultati previsti</u>:

Le immagini vengono salvate senza errori.

<u>Risultati effettivi</u>:

&quot;*Impossibile salvare il prodotto*&quot; viene restituito un errore di tanto in tanto.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
