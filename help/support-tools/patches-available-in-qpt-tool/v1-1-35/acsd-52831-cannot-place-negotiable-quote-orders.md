---
title: '"ACSD-52831: impossibile inserire ordini di preventivo negoziabili quando [!DNL Google reCAPTCHA v3 Invisible] abilitato'''
description: Applicare la patch ACSD-52831 per risolvere il problema di Adobe Commerce che non consente di inserire ordini di preventivo negoziabili quando [!DNL Google reCAPTCHA v3 Invisible] è abilitato.
feature: Quotes, B2B, Checkout
role: Admin
exl-id: 80cf5592-0784-4b37-8373-abec0847a9f0
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# ACSD-52831: impossibile inserire ordini di preventivo negoziabili quando [!DNL Google reCAPTCHA v3 Invisible] abilitato

La patch ACSD-52831 risolve il problema che impediva di inserire ordini di preventivo negoziabili quando [!DNL Google reCAPTCHA v3 Invisible] è abilitato. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.35. L’ID della patch è ACSD-52831. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Impossibile inserire ordini di preventivo negoziabili quando [!DNL Google reCAPTCHA v3 Invisible] è abilitato.

<u>Passaggi da riprodurre</u>:

1. Abilita la funzione delle virgolette B2B.
1. Abilita [!DNL Google reCAPTCHA v3 Invisible] sul vetrina per abilitare gli ordini di pagamento/collocazione.
1. Generare un preventivo e procedere al pagamento con tale preventivo.
1. Non potrai effettuare un ordine a causa dell’errore CAPTCHA.

<u>Risultati previsti</u>:

Il preventivo procede al pagamento.

<u>Risultati effettivi</u>:

Viene visualizzato l’errore *Convalida reCAPTCHA non riuscita, riprova*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
