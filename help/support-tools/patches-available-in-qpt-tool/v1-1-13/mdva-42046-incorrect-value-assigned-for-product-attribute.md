---
title: "MDVA-42046: valore non corretto assegnato per l'attributo product"
description: La patch di MDVA-42046 risolve il problema relativo all'assegnazione di un valore non corretto per l'attributo product durante l'aggiornamento di un prodotto con un campo di immissione data. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13. L'ID della patch è MDVA-42046. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: 837f5582-849c-43a3-ae02-87f71fb96061
feature: Attributes, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 0%

---

# MDVA-42046: valore non corretto assegnato per l&#39;attributo di prodotto

La patch di MDVA-42046 risolve il problema relativo all&#39;assegnazione di un valore non corretto per l&#39;attributo product durante l&#39;aggiornamento di un prodotto con un campo di immissione data. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13. L&#39;ID della patch è MDVA-42046. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.4 - 2.3.5-p2 e 2.4.0 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Dopo aver salvato un prodotto con i campi `news_from_date` e/o `news_to_date`, i valori di tali campi vengono ripristinati sui valori predefiniti.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto semplice.
1. Esporta il prodotto creato al passaggio 1.
1. Nel file CSV esportato inserire alcuni valori nei campi `news_from_date` e `news_to_date`. Ad esempio, 2021-05-15 e 2021-06-18.
1. Importa il prodotto utilizzando il file CSV modificato.
1. Aggiungere ulteriori colonne &quot;Imposta prodotto come nuovo da data&quot; e &quot;Imposta prodotto come nuovo a data&quot; alla griglia del prodotto.
1. Apri la pagina di modifica del prodotto e, senza modifiche, fai clic su **Salva**.
1. Torna alla griglia del prodotto e controlla i dati del prodotto.

<u>Risultati previsti</u>:

Sia &quot;Imposta prodotto come nuovo da data&quot; che &quot;Imposta prodotto come nuovo a data&quot; sono gli stessi di prima del salvataggio.

<u>Risultati effettivi</u>:

* I valori nelle colonne &quot;Imposta prodotto come nuovo da data&quot; e &quot;Imposta prodotto come nuovo a data&quot; vengono modificati.

* La colonna &quot;Imposta prodotto come nuovo da data&quot; mostra la data corrente e la colonna &quot;Imposta prodotto come nuovo a data&quot; è vuota.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella documentazione per gli sviluppatori.
