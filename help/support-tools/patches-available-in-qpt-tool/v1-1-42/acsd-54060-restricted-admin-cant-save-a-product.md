---
title: "ACSD-54060: l’amministratore con restrizioni non può salvare un prodotto se è figlio di un altro prodotto"
description: Applica la patch ACSD-54060 per risolvere il problema di Adobe Commerce, a causa del quale un amministratore con restrizioni non è in grado di salvare un prodotto se è figlio di un altro prodotto assegnato a un ambito diverso.
feature: Admin Workspace, Roles/Permissions, Products
role: Admin, Developer
exl-id: 28fa3c99-f2b6-4c6d-955a-bd6638a1b077
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-54060: l’amministratore con restrizioni non può salvare il prodotto se è figlio di un altro prodotto

La patch ACSD-54060 risolve il problema che impedisce a un amministratore con restrizioni di salvare un prodotto se è figlio di un altro prodotto assegnato a un ambito diverso. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42. L’ID della patch è ACSD-54060. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Un amministratore con restrizioni non è in grado di salvare un prodotto se è figlio di un altro prodotto assegnato a un ambito diverso.

<u>Passaggi da riprodurre</u>:

1. Crea un altro sito web.
1. Crea un prodotto semplice e assegnalo a entrambi i siti web.
1. Crea un prodotto configurabile con il prodotto semplice come unica variante e assegna il prodotto configurabile solo al sito Web predefinito.
1. Crea un utente amministratore con restrizioni con accesso solo al secondo sito Web.
1. Accedi come utente amministratore con restrizioni.
1. Prova a modificare il nome del prodotto semplice nel secondo ambito del sito web.

<u>Risultati previsti</u>:

L’amministratore con restrizioni può modificare il nome del prodotto.

<u>Risultati effettivi</u>:

Si verifica un errore: *Sono necessarie altre autorizzazioni per visualizzare questo elemento*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
