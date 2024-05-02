---
title: '"MDVA-42520: aliquota applicata due volte quando si utilizza "Abilita commercio transfrontaliero""'
description: La patch MDVA-42520 risolve il problema dell'applicazione dell'aliquota due volte quando si utilizza **Abilita commercio transfrontaliero**. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11. L'ID della patch è MDVA-42520. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: c1ca44eb-fe92-4f28-807a-3a4563433386
feature: Catalog Management, Orders, Taxes
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---

# MDVA-42520: aliquota applicata due volte quando si utilizza &quot;Abilita commercio transfrontaliero&quot;

La patch MDVA-42520 risolve il problema dell&#39;applicazione dell&#39;aliquota due volte quando **Abilitare il commercio transfrontaliero** viene utilizzato. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11. L&#39;ID della patch è MDVA-42520. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;aliquota viene applicata due volte quando **Abilitare il commercio transfrontaliero** viene utilizzato.

<u>Passaggi da riprodurre</u>:

1. Abilita **Azienda**, **Catalogo condiviso**, e **Citazione**
1. Configura le imposte in base alla schermata. Assicurati di abilitare **Commercio transfrontaliero**.

   ![impostazioni imposta](/help/support-tools/patches-available-in-qpt-tool/assets/tax_settings_1.png){width="700"}

1. Creare un&#39;aliquota fiscale per la Germania (10%).
1. Creare una regola fiscale per applicare l&#39;aliquota.
1. Crea una società e un catalogo condiviso personalizzato.
1. Crea un prodotto con un prezzo di 100 e includilo nel catalogo condiviso personalizzato con uno sconto del 20%.
1. Crea un cliente con un indirizzo in tedesco e assegnalo all’azienda
1. Aggiungi 10 prodotti alla scheda come cliente.
1. Vai al carrello e richiedi un preventivo.
1. Apri questo preventivo sul backend e prova ad aggiungere un ulteriore sconto del 10%.

<u>Risultati previsti</u>:

Subtotale preventivo (imposte incluse) e Totale complessivo preventivo (imposte incluse) = $ 720

<u>Risultati effettivi</u>:

Subtotale preventivo (imposte incluse) e Totale complessivo preventivo (imposte incluse) = 649,50 $.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
