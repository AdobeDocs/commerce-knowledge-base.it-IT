---
title: "MDVA-39713: l'utente può modificare l'ora di inizio dell'aggiornamento pianificato attivo"
description: La patch MDVA-39713 risolve il problema che consente all'utente di modificare l'ora di inizio di un aggiornamento pianificato attivo. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12. L'ID della patch è MDVA-39713. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: c7221fdb-5fc0-4179-8d4c-c9e1f0d00692
feature: CMS
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# MDVA-39713: l&#39;utente può modificare l&#39;ora di inizio dell&#39;aggiornamento pianificato attivo

La patch MDVA-39713 risolve il problema che consente all&#39;utente di modificare l&#39;ora di inizio di un aggiornamento pianificato attivo. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12. L&#39;ID della patch è MDVA-39713. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.3.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’utente può modificare l’ora di inizio di un aggiornamento pianificato attivo.

<u>Passaggi da riprodurre</u>:

1. Creare nuove pagine CMS.
1. Seleziona **Pianifica nuovo aggiornamento** e imposta la **Data inizio** su +1 minuto corrente.
1. Attivare Aggiornamento pianificato eseguendo il comando `bin/magento cron:run --group=staging` nell&#39;ambiente locale. Attendi alcuni minuti e controlla se la pianificazione è attiva.
1. Quando la pianificazione è attiva, aggiorna la pagina.
1. Fare clic su **Visualizza/Modifica** nella sezione Modifiche pianificate.
1. Modifica l’ora aggiungendo +2 minuti e salva la modifica.
1. Salva la pagina CMS.
1. Eseguire nuovamente il comando seguente: `bin/magento cron:run --group=staging`.
1. Fai clic su **Visualizza/Modifica** dell&#39;aggiornamento pianificato.

<u>Risultati previsti</u>:

L’utente non è in grado di modificare l’ora di inizio di un aggiornamento pianificato attivo.

<u>Risultati effettivi</u>:

L&#39;utente riceve un errore simile a *Elemento (Magento\Cms\Model\Page) con lo stesso ID &quot;11&quot; già esistente.*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella documentazione per gli sviluppatori.
