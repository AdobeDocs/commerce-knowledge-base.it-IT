---
title: 'MDVA-41236: impossibile creare nuovi aggiornamenti pianificati o modificare quelli esistenti per il prodotto'
description: La patch MDVA-41236 risolve il problema che impediva agli utenti di creare nuovi aggiornamenti pianificati o di modificare quelli esistenti per il prodotto, se la "Data di fine" era stata precedentemente rimossa. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.5. L'ID della patch è MDVA-41236. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: 00d6c0af-f248-49f6-aaa2-3ae3c0294832
feature: Products, Staging
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# MDVA-41236: impossibile creare nuovi aggiornamenti pianificati o modificare quelli esistenti per il prodotto

La patch MDVA-41236 risolve il problema che impediva agli utenti di creare nuovi aggiornamenti pianificati o di modificare quelli esistenti per il prodotto, se la &quot;Data di fine&quot; era stata precedentemente rimossa. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.5. L&#39;ID della patch è MDVA-41236. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli utenti non possono creare nuove pianificazioni o modificare quelle esistenti per i prodotti se la &quot;Data di fine&quot; è stata precedentemente rimossa.

<u>Passaggi da riprodurre</u>:

1. Creare un prodotto con lo stato impostato su *disable*.
1. Aggiungi un aggiornamento pianificato per abilitare questo prodotto.
   * Aggiungere date di inizio e fine future.
1. Modifica l&#39;aggiornamento pianificato rimuovendo la **data di fine**.
1. Modifica di nuovo la pianificazione e prova ad aggiungere una **data di fine**. Si verificherà un errore.
1. Aggiorna la pagina e torna a **Modifica aggiornamento pianificato**.
1. Fai clic su **Rimuovi dall&#39;aggiornamento** > **Elimina l&#39;aggiornamento**.
1. Ora l’aggiornamento pianificato non dovrebbe essere visibile nella parte superiore della pagina di modifica del prodotto.
1. Prova a creare un nuovo aggiornamento pianificato che si sovrappone alla durata precedente.

<u>Risultati previsti</u>:

* Il passaggio 4 non contiene errori. L’amministratore è in grado di aggiornare l’aggiornamento pianificato senza errori, in quanto la pianificazione non è ancora attiva.
* L’utente amministratore può eliminare l’aggiornamento precedente e crearne uno nuovo.

<u>Risultati effettivi</u>:

Gli utenti ricevono il seguente messaggio di errore:

*errore: aggiornamento futuro già esistente in questo intervallo di tempo. Impostare un intervallo diverso e riprovare.*


## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
