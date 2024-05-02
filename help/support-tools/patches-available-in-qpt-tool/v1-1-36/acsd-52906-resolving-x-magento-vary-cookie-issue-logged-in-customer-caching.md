---
title: "ACSD-52906: risoluzione del problema relativo ai cookie X-Magento-Vary per il caching dei clienti connessi"
description: Applica la patch ACSD-52906 per risolvere il problema di Adobe Commerce, in cui il cookie X-Magento-Vary non è impostato correttamente per i clienti connessi.
feature: Cache
role: Admin, Developer
exl-id: 863e0808-9208-467d-8d56-9dd7a7f4354d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# ACSD-52906: Risoluzione del problema relativo ai cookie X-Magento-Vary per i clienti connessi

La patch ACSD-52906 risolve il problema relativo all’impostazione errata del cookie X-Magento-Vary per i clienti connessi. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.36. L’ID della patch è ACSD-52906. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il cookie X-Magento-Vary non è impostato correttamente per i clienti connessi che appartengono allo stesso segmento di clienti, causando la memorizzazione in cache non corretta per alcune pagine.

<u>Prerequisiti</u>:

I moduli Adobe Commerce Inventory management (MSI) sono installati e abilitati.

<u>Passaggi da riprodurre</u>:

1. Configura [!DNL Varnish] o [!DNL Fastly] cache.
1. Creare un nuovo segmento di clienti e assegnarlo al *Registrato* clienti.
1. Creare due clienti, ad esempio cliente1 e cliente2.
1. Cancella la cache.
1. Accedi come cliente1 e vai alla home page.
1. Apri una pagina in incognito sul browser.
1. Vai a qualsiasi pagina diversa dalla home page.
1. Accedere come cliente2.
1. Passa alla home page.
1. Verifica se la pagina è memorizzata nella cache nella console di sviluppo del browser.

<u>Risultati previsti</u>:

La pagina viene recuperata dalla cache.

<u>Risultati effettivi</u>:

La pagina non è memorizzata in cache.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
