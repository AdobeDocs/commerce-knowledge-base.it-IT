---
title: "MDVA-40619: le modifiche della gerarchia interrompono la pagina CMS durante la modifica in linea e generano l’errore 500"
description: La patch di MDVA-40619 risolve il problema relativo alle modifiche apportate alla gerarchia delle pagine CMS che causano l'interruzione della modifica in linea della pagina CMS e la generazione di "errore 500". Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5. L'ID della patch è MDVA-40619. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
exl-id: c003d845-1ba0-49c0-9f1a-a4b0ec00f30c
feature: CMS
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# MDVA-40619: le modifiche della gerarchia interrompono la pagina CMS durante la modifica in linea e generano l&#39;errore 500

La patch di MDVA-40619 risolve il problema relativo alle modifiche apportate alla gerarchia delle pagine CMS che causano l&#39;interruzione della modifica in linea della pagina CMS e la generazione di &quot;errore 500&quot;. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5. L&#39;ID della patch è MDVA-40619. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le modifiche alla gerarchia delle pagine CMS interrompono la modifica in linea della pagina CMS e generano &quot;errore 500&quot;.

<u>Passaggi da riprodurre</u>:

1. Vai a Pannello di amministrazione > **Contenuto** > **Gerarchia**.
1. Seleziona &quot;Visualizzazione store predefinita&quot;.
1. Deselezionare &quot;Use the parent node hierarchy&quot; (Utilizza la gerarchia dei nodi padre).
1. Seleziona la pagina manualmente e fai clic su **Salva**.
1. Quindi Vai a **Contenuto** > **Pagine**.
1. Prova a modificare qualsiasi pagina CMS dalla griglia.
1. Fai clic su **Salva**.

<u>Risultati previsti</u>:

La pagina è stata salvata.

<u>Risultati effettivi</u>:

Viene visualizzato il seguente errore:

*Un problema tecnico con il server ha creato un errore. Riprova a continuare quello che stavi facendo. Se il problema persiste, riprovare più tardi.*

`Error: Call to a member function getData() on null in /magento2ee/app/code/Magento/VersionsCms/Controller/Adminhtml/Cms/Page/InlineEdit/Plugin.php:62`

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
