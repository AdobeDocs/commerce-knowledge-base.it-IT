---
title: 'MDVA-33606: errore durante il salvataggio della pagina CMS assegnata alla gerarchia'
description: La patch di MDVA-33606 risolve il problema relativo all'errore *Unique constraint viola found* (Violazione di vincolo univoca trovata) durante il salvataggio di una pagina CMS assegnata alla struttura gerarchica. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.3. L'ID della patch è MDVA-33606. Il problema è stato risolto in Adobe Commerce 2.4.3.
exl-id: cdefece5-6d13-4003-87e9-810c665e940c
feature: CMS
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# MDVA-33606: errore durante il salvataggio della pagina CMS assegnata alla gerarchia

La patch MDVA-33606 risolve il problema relativo all&#39;errore *Rilevata violazione di vincolo univoco* durante il salvataggio di una pagina CMS assegnata alla struttura gerarchica. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.3. L&#39;ID della patch è MDVA-33606. Il problema è stato risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1-2.4.2-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando si tenta di salvare una pagina CMS assegnata alla struttura gerarchica, agli utenti viene visualizzato il seguente messaggio di errore: *È stata rilevata una violazione di vincolo univoco*.

<u>Passaggi da riprodurre</u>:

1. Crea una nuova pagina CMS. Imposta l&#39;ambito su Tutte le visualizzazioni dello store. Pagina 1 di CMS.
1. Crea una nuova visualizzazione store. Questa è la tua Store View 2.
1. Vai a **Contenuto** > **Gerarchia** > Aggiungi la pagina 1 di CMS alla struttura gerarchica.
1. Modificare l&#39;ambito in Visualizzazione archivio 2.
   * Deselezionare &quot;Use the parent node hierarchy&quot; (Utilizza la gerarchia dei nodi padre).
   * Aggiungere CMS Page 1 a questo ambito e salvarlo.
1. Ora modifica l’ambito in Visualizzazione archivio predefinita.
   * Deselezionare &quot;Use the parent node hierarchy&quot; (Utilizza la gerarchia dei nodi padre).
   * Aggiungere CMS Page 1 a questo ambito e salvarlo.
1. Vai a **Contenuto** > **Pagine** > **Aggiungi nuova pagina**.
   * Assegna alla pagina il titolo Pagina 2.
   * Nella sezione Pagina in siti Web, assegna a Tutte le visualizzazioni dello store ed entrambe le visualizzazioni dello store (Visualizzazione store predefinita e Visualizzazione store 2) e fai clic su **Salva pagina**.
1. Nella pagina di modifica di CMS, apri la scheda Gerarchia.
   * Assegna pagina 2 al nodo Visualizzazione archivio 2, al nodo Predefinito e al nodo Tutti i siti Web.

<u>Risultati previsti</u>:

Puoi assegnare la pagina CMS a tutti e tre i nodi senza alcun errore.

<u>Risultati effettivi</u>:

Viene visualizzato il seguente errore: *È stata rilevata una violazione di vincolo univoco*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento Quality Patches: è stato introdotto un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
