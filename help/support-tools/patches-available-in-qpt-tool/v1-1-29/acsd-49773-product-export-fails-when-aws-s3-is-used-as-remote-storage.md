---
title: "ACSD-49773: l’esportazione del prodotto non riesce quando AWS S3 viene utilizzato come archiviazione remota"
description: Applica la patch ACSD-49773 per risolvere il problema di Adobe Commerce in cui l’esportazione del prodotto non riesce quando AWS S3 viene utilizzato come archiviazione remota.
exl-id: 5ef853c3-8080-4403-836b-6fff93ec71c6
feature: Data Import/Export, Iaas, Products, Storage
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-49773: l’esportazione del prodotto non riesce quando AWS S3 viene utilizzato come archiviazione remota

La patch ACSD-49773 risolve il problema se l’esportazione del prodotto non riesce quando AWS S3 viene utilizzato come archivio remoto. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29. L’ID della patch è ACSD-49773. Il problema è stato risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.5-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’esportazione del prodotto non riesce quando AWS S3 viene utilizzato come archiviazione remota.

<u>Passaggi da riprodurre</u>:

1. Installa un profilo dati di grandi dimensioni.
1. Crea un account AWS e configura un bucket S3 e un utente IAM.
1. Aggiorna `app/etc/env.php` con le configurazioni.
1. Esegui `bin/magento setup:upgrade`.
1. Vai al back-end ed esegui un’esportazione completa del prodotto.
1. Monitora lo stato dei messaggi della coda da `[queue_message_status]` tabella.
1. Controllare i registri di sistema.

<u>Risultati previsti</u>:

L’esportazione del prodotto termina senza errori.

<u>Risultati effettivi</u>:

Nei registri di sistema viene registrato un errore.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
