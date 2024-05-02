---
title: "ACSD-51102: regola del catalogo applicata a un numero elevato di prodotti non indicizzati correttamente"
description: Applica la patch ACSD-51102 per risolvere il problema di Adobe Commerce, in cui una regola di catalogo applicata a un numero elevato di prodotti non viene indicizzata correttamente quando la regola è abilitata da un aggiornamento pianificato.
feature: Catalog Management, Products
role: Admin
exl-id: 5c1c5f9c-9cce-4b11-8058-0e12a4bf93fd
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# ACSD-51102: regola di catalogo applicata a un numero elevato di prodotti non indicizzati correttamente

La patch ACSD-51102 risolve il problema relativo a una regola di catalogo applicata a un numero elevato di prodotti che non viene indicizzata correttamente quando la regola è abilitata da un aggiornamento pianificato. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33. L’ID della patch è ACSD-51102. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Una regola di catalogo applicata a un numero elevato di prodotti non viene indicizzata correttamente quando viene abilitata da un aggiornamento pianificato.

Prerequisiti:

* Il processo Cron viene configurato ed eseguito ogni minuto.

<u>Passaggi da riprodurre</u>:

1. Crea un catalogo di grandi dimensioni con migliaia di prodotti per ottenere il tempo di esecuzione per *regola catalogo* indici superiori a 120 secondi quando le regole di catalogo vengono abilitate.
2. Creare due regole di catalogo con *Attivo* Stato impostato su *No*.  Ad esempio: *Prova 1* e *Prova 2*. Ogni regola deve influire su tutti i prodotti del catalogo e causare l’esecuzione dell’indicizzatore per più di 120 secondi.
3. Assicurati che lo stato dell’indicizzatore sia *Pronto*.
4. Crea aggiornamenti pianificati per abilitare queste due regole. *Prova 2* la pianificazione deve iniziare poco dopo *Prova 1*. Ad esempio, con una differenza di 1 minuto.
5. Controlla i prezzi dei prodotti sul Negozio.

<u>Risultati previsti</u>

Vengono applicati sconti da entrambe le regole.

<u>Risultati effettivi</u>

Viene applicato solo il primo sconto regola.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) nel [!DNL Quality Patches Tool] guida.
