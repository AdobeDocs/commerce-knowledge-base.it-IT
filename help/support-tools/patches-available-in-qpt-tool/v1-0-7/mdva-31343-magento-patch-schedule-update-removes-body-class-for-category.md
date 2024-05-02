---
title: "Patch MDVA-31343: aggiornamento pianificazione rimuove la classe body per la categoria"
description: La patch MDVA-31343 risolve il problema relativo alla rimozione della classe CSS del corpo del layout assegnato per una categoria durante l'aggiornamento pianificato. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.2.
exl-id: 50dbff01-cb77-4cac-b90e-5c4b06f5e4e7
feature: Cache, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# Patch MDVA-31343: aggiornamento pianificazione rimuove la classe body per la categoria

La patch MDVA-31343 risolve il problema relativo alla rimozione della classe CSS del corpo del layout assegnato per una categoria durante l&#39;aggiornamento pianificato. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.2.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.5-p2

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud e Adobe Commerce on-premise 2.3.4 - 2.3.5-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La classe del corpo del layout viene rimossa dalla categoria dopo l’aggiornamento pianificato.

<u>Passaggi da riprodurre</u>:

1. Nell’amministratore di Commerce, crea una categoria.
1. Imposta **Layout** = *Categoria — Larghezza intera* nel **Progettazione** sezione.
1. Salva la categoria.
1. Vai alla pagina front-end delle categorie. Nell’avviso di origine della pagina

   ```css
   page-layout-category-full-width
   ```

   Classe CSS.
1. Sotto **CATALOGO** > **Categoria**, fai clic su **Pianifica nuovo aggiornamento** nel *Modifiche pianificate* per la nuova categoria.
1. Attendi l’avvio dell’aggiornamento pianificato, esegui cron e svuota cache.
1. Vai alla pagina della categoria sul front-end e controlla l’origine della pagina.

<u>Risultati previsti</u>:

Nel corpo della pagina viene visualizzato il comando

```css
page-layout-category-full-width
```

Classe CSS.

<u>Risultati effettivi</u>:

Nel corpo della pagina viene visualizzato il comando

```css
page-layout-2columns-left
```

Classe CSS, impostazione predefinita per la pagina delle categorie.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
