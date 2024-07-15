---
title: "MDVA-29954: indirizzo errato inviato messaggio di posta elettronica di registrazione utente nuova società"
description: La patch MDVA-29954 risolve il problema relativo all'invio delle e-mail "Nuova richiesta di registrazione società" e "Sei stato collegato a un'azienda" da un indirizzo e-mail errato. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8. Il problema è stato risolto in Adobe Commerce 2.4.2.
exl-id: 9b3d1b93-3fe6-40a0-a68a-3e3d789c6d66
feature: B2B, Communications, Companies
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# MDVA-29954: indirizzo errato inviato messaggio di posta elettronica di registrazione utente nuova società

La patch MDVA-29954 risolve il problema relativo all&#39;invio delle e-mail &quot;Nuova richiesta di registrazione società&quot; e &quot;Sei stato collegato a un&#39;azienda&quot; da un indirizzo e-mail errato. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8. Il problema è stato risolto in Adobe Commerce 2.4.2.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.3.5-p2, 2.4.0 e 2.4.1.

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Prerequisiti</u>:

Installa Adobe Commerce con B2B, con **funzionalità B2B** e **società** abilitate.

<u>Passaggi da riprodurre</u>:

1. Fai clic sul menu a discesa **Crea account** nella vetrina e seleziona **Crea nuovo account società**.
1. Compila i campi obbligatori e registra l’account.
1. Abilita la **società** dal backend (**cliente** > **società**).
1. Controlla l’indirizzo e-mail utilizzato per la registrazione.
1. Impostare la **password amministratore società** seguendo le istruzioni inviate tramite posta elettronica.
1. Accedi al front-end con la **password amministratore società**.
1. Crea un nuovo **Utente società** in **Account personale** > **Utenti società** > **Aggiungi nuovo utente**.
1. Vai a **Archivi** > **Configurazioni** > **Indirizzi e-mail dell&#39;archivio generale** > **Contatto generale** e controlla **E-mail mittente**.
1. Vai all&#39;e-mail utilizzata per registrare il **nuovo utente** nel passaggio 7.

<u>Risultati previsti</u>:

L&#39;e-mail &quot;Sei stato collegato a un&#39;azienda&quot; viene inviata da un indirizzo e-mail con lo stesso valore di **E-mail mittente** nel passaggio 8.

<u>Risultati effettivi</u>:

L&#39;e-mail &quot;Sei stato collegato a un&#39;azienda&quot; viene inviata dall&#39;amministratore **Aziende**.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
