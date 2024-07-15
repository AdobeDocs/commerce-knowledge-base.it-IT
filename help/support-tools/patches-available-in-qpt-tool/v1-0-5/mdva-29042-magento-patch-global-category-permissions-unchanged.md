---
title: "MDVA-29042: autorizzazioni categoria globali invariate"
description: La patch MDVA-29042 risolve il problema relativo alla modifica automatica delle autorizzazioni del catalogo in "*Consenti*" dopo l'aggiunta di un nuovo prodotto al catalogo condiviso in Amministrazione Commerce. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5. Il problema è stato risolto in Adobe Commerce 2.3.6 con l’estensione B2B.
exl-id: 491b8881-87ec-4820-8f87-54961682e961
feature: Catalog Management, Categories, Customer Service, Roles/Permissions
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# MDVA-29042: autorizzazioni categoria globali invariate

La patch di MDVA-29042 risolve il problema relativo alla modifica automatica delle autorizzazioni del catalogo in &quot;*Consenti*&quot; dopo l&#39;aggiunta di un nuovo prodotto al catalogo condiviso in Amministrazione Commerce. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5. Il problema è stato risolto in Adobe Commerce 2.3.6 con l’estensione B2B.

## Prodotti e versioni interessati

Adobe Commerce (tutti i metodi di implementazione) da 2.3.3 a 2.3.4-p2 con estensione B2B

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Deselezionando un gruppo di clienti dalle autorizzazioni della categoria globale in Commerce Admin, questo non viene impostato automaticamente su &quot;*Nega*&quot; nelle autorizzazioni della categoria.

<u>Prerequisiti</u>:

* Istanza B2B con un gruppo di clienti definito e selezionato in **ARCHIVI** > **Configurazione** > **CATALOGO** > **Catalogo** > **Autorizzazioni categoria** per:
   * **Consenti esplorazione categoria**
   * **Visualizza prezzi prodotti**
   * **Consenti aggiunta al carrello**
* In ogni **Categoria**, il gruppo di clienti è definito come &quot;*Consenti*&quot; per:
   * **Navigazione nella categoria**
   * **Visualizza prezzi prodotti**
   * **Aggiungi al carrello**

<u>Passaggi da riprodurre</u>:

1. In Amministrazione Commerce, vai a **ARCHIVI** > **Configurazione** > **CATALOGO** > **Catalogo** > **Autorizzazioni categoria** e deseleziona il gruppo di clienti da:
   * **Consenti esplorazione categoria**
   * **Visualizza prezzi prodotti**
   * **Consenti aggiunta al carrello**
1. Fare clic sul pulsante **Salva configurazione**.
1. Attendere l&#39;esecuzione degli indicizzatori.
1. Osserva **CATALOGO** > **Categorie** > **Autorizzazioni categoria**.

<u>Risultati previsti</u>:

**Autorizzazioni categoria** verrà impostato su &quot;*Nega*&quot; per tutte le categorie per il gruppo di clienti.

<u>Risultati effettivi</u>:

Nessuna modifica alle autorizzazioni di categoria per il gruppo di clienti.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.

Per ulteriori informazioni sulle funzionalità aziendali B2B, consulta i seguenti articoli nella documentazione per gli sviluppatori:

* [Guida per gli sviluppatori B2B](https://devdocs.magento.com/guides/v2.4/b2b/bk-b2b.html)
* [Gestione ruoli società](https://devdocs.magento.com/guides/v2.4/b2b/roles.html)
* [Riferimento dei percorsi di configurazione dell&#39;estensione Adobe Commerce Enterprise B2B](https://devdocs.magento.com/guides/v2.4/config-guide/prod/config-reference-b2b.html)
