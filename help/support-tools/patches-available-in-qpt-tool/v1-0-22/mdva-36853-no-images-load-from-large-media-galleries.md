---
title: "MDVA-36853: nessuna immagine caricata da gallerie di file multimediali di grandi dimensioni"
description: La patch MDVA-36853 risolve il problema quando non vengono caricate immagini, poiché il widget raccolta file multimediali di Page Builder non viene caricato quando si dispone di una directory multimediale di grandi dimensioni.
exl-id: 64e089d9-d443-4aa7-8e04-a3598b05958d
feature: CMS, Cache, Media
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# MDVA-36853: nessuna immagine caricata da gallerie multimediali di grandi dimensioni

La patch MDVA-36853 risolve il problema quando non vengono caricate immagini, poiché il widget raccolta file multimediali di Page Builder non viene caricato quando si dispone di una directory multimediale di grandi dimensioni.

Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22. L&#39;ID della patch è MDVA-36853. Il problema è pianificato per la risoluzione in Adobe Commerce versione 2.4.3.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:** Adobe Commerce sull’infrastruttura cloud 2.4.2

**Compatibile con le versioni di Adobe Commerce:** Adobe Commerce on-premise e Adobe Commerce sull’infrastruttura cloud 2.4.2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Passaggi da riprodurre</u>:

1. Imposta **Abilita raccolta file multimediali obsoleti** = *Sì* in **Admin (Amministrazione) > Stores (Archivi) > Configuration (Configurazione) > Advanced (Avanzate) > System (Sistema) > Media gallery (Galleria di supporti)**.
1. Accedi a **Contenuto > Blocchi** e creare un nuovo blocco CMS o modificare un blocco CMS esistente.
1. Fai clic sul pulsante **Modifica con Generatore di pagine** pulsante.
1. Aggiungi un elemento multimediale.
1. Fai clic sul pulsante **Seleziona dalla raccolta** pulsante.

<u>Risultati previsti</u>:

Il widget della galleria di file multimediali e le immagini della galleria di file multimediali vengono entrambi caricati, come previsto.

<u>Risultati effettivi</u>:

Il widget della galleria di file multimediali e le immagini della galleria di file multimediali non vengono caricati quando si dispone di un grande `pub/media/catalog/product/cache/` directory.

## Applicare la patch

Per applicare singole patch, utilizzare i seguenti collegamenti, a seconda del prodotto Adobe Commerce:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili nello strumento QPT, consultare [Patch disponibili nello strumento QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sezione.
