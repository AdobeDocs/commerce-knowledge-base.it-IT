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

La patch MDVA-29954 risolve il problema relativo all&#39;invio delle e-mail &quot;Nuova richiesta di registrazione società&quot; e &quot;Sei stato collegato a un&#39;azienda&quot; da un indirizzo e-mail errato. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8. Il problema è stato risolto in Adobe Commerce 2.4.2.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.3.5-p2, 2.4.0 e 2.4.1.

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Prerequisiti</u>:

Installare Adobe Commerce con B2B, **Caratteristiche B2B** e **Azienda** abilitato.

<u>Passaggi da riprodurre</u>:

1. Fai clic sul pulsante **Crea account** nella vetrina e seleziona **Crea nuovo account società**.
1. Compila i campi obbligatori e registra l’account.
1. Abilita **Azienda** dal backend (**Cliente** > **Aziende**).
1. Controlla l’indirizzo e-mail utilizzato per la registrazione.
1. Imposta il **Password amministratore società** seguendo le istruzioni inviate via e-mail.
1. Accedi al front-end con **Password amministratore società**.
1. Crea un nuovo **Utente società** in **Il mio account** > **Utenti società** > **Aggiungi nuovo utente**.
1. Vai a **Negozi** > **Configurazioni** > **Indirizzi e-mail del Negozio generale** > **Contatto generale**, e verifica **E-mail mittente**.
1. Vai all’e-mail utilizzata per registrare il **Nuovo utente** al punto 7.

<u>Risultati previsti</u>:

L’e-mail &quot;Sei stato collegato a un’azienda&quot; viene inviata da un indirizzo e-mail con lo stesso valore di per **E-mail mittente** al punto 8.

<u>Risultati effettivi</u>:

L’e-mail &quot;Sei stato collegato a un’azienda&quot; viene inviata dal **Amministratore società** e-mail.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
