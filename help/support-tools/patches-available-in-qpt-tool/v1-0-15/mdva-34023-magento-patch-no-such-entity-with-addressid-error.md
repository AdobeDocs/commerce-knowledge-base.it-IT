---
title: 'Patch MDVA-34023: errore "Nessuna entità con ID indirizzo"'
description: La patch MDVA-34023 risolve il problema in cui gli errori "No such entity with addressId" (Nessuna entità con ID indirizzo) si verificano in modo casuale sul browser web di un cliente.
exl-id: bdf8f97d-856a-4dd7-bf21-941d1493496c
feature: Variables
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# Patch MDVA-34023: errore &quot;Nessuna entità di questo tipo con ID indirizzo&quot;

La patch di MDVA-34023 risolve il problema che causa la presenza casuale di `No such entity with addressId` errori nel browser Web di un cliente.

Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.15. Il problema è pianificato per la risoluzione in Adobe Commerce versione 2.4.3.

## Prodotti e versioni interessati

**La patch è stata creata per Adobe Commerce versione:** Adobe Commerce sull&#39;infrastruttura cloud 2.3.1

**Compatibile con le versioni di Adobe Commerce:** Adobe Commerce su infrastruttura cloud e Adobe Commerce on-premise 2.3.0 - 2.4.2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Passaggi da riprodurre</u>:

1. Vai a **Archivi** > **Impostazioni** > **Configurazione** > **Scheda Clienti** > **Carrello acquisti permanente**.
1. Imposta **Abilita persistenza** = *Sì*, imposta **Cancella persistenza alla disconnessione** = *No*.    ![persistent_shopping_cart_magento_2.4.1.png](/help/support-tools/patches-available-in-qpt-tool/assets/persistent_shopping_cart_magento_2.4.1.png)
1. Crea un nuovo cliente e definisci gli indirizzi predefiniti di spedizione e fatturazione.
1. Disconnetti.
1. Accedi con la casella di controllo **Ricorda utente** selezionata.
1. Andare alla tabella del database `customer_entity` e modificare gli ID `default_billing` e `default_shipping` in ID non esistenti.
1. Disconnetti.

<u>Risultati previsti</u>:

Non viene visualizzato alcun errore, come previsto.

<u>Risultati effettivi</u>:

Viene generato il registro eccezioni:

```php
Exception.log:
{"0":"No such entity with addressId = XXXXX","1":"#0 /vendor\/magento\/module-customer\/Model\/AddressRegistry.php(49): Magento\\Framework
Exception
NoSuchEntityException::singleField('addressId', 'XXXXX')
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili nello strumento QPT, fare riferimento alla sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
