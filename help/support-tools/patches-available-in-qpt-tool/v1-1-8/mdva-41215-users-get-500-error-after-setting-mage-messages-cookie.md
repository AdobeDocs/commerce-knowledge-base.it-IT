---
title: '''MDVA-41215: errore 500 per gli utenti dopo l''impostazione del cookie "mage-messages"'''
description: La patch MDVA-41215 risolve il problema che causa l'errore 500 degli utenti dopo aver impostato il cookie "mage-messages", se esiste già, ma non sono presenti nuovi messaggi. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8. L'ID della patch è MDVA-41215. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
exl-id: 93555984-1eed-4866-ab49-5467f9afd124
feature: Configuration
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# MDVA-41215: errore 500 dopo l&#39;impostazione del cookie &quot;mage-messages&quot;

La patch MDVA-41215 risolve il problema che causa l&#39;errore 500 degli utenti dopo aver impostato il cookie &quot;mage-messages&quot;, se esiste già, ma non sono presenti nuovi messaggi. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8. L&#39;ID della patch è MDVA-41215. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli utenti ricevono l’errore 500 dopo aver impostato il cookie &quot;mage-messages&quot; se esiste già, ma non ci sono nuovi messaggi.

<u>Passaggi da riprodurre</u>:

1. Vai a **../cliente/account/accesso**.
1. Apri la scheda Rete negli strumenti di sviluppo del browser (assicurati che sia selezionato l’opzione mantieni registro).
1. Compila il modulo con valori non validi (l’accesso non dovrebbe riuscire).
1. Clic **Invia**.
1. Copia come cURL la prima richiesta dalla scheda di rete e cerca i valori PHPSESSID e form_key.
1. Sostituisci i valori PHPSESSID e form_key nella richiesta cURL aggiornata e inviala.

```curl -sSL -D - 'http://magento24.loc/customer/account/loginPost/' -i -o /dev/null \
--data-raw 'form_key=i4UVctCCEdAlG13P&login%5Busername%5D=aaa%40bbb.ccc&login%5Bpassword%5D=qwerty' \
--header 'cookie: mage-messages=%5B%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%5D; PHPSESSID=l5575pntrhopuk3ld6maf5aa2m; mage-messages=%5B%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%2C%7B%22type%22%3A%22error%22%2C%22text%22%3A%22Invalid%20Form%20Key.%20Please%20refresh%20the%20page.%22%7D%5D; private_content_version=0de5bf3a3e27e966dd5d6c1ee84e27a7'
```

<u>Risultati previsti</u>:

Utenti ottengono `HTTP/1.1 200 OK`

<u>Risultati effettivi</u>:

Utenti ottengono `HTTP/1.1 500 Internal Server Error`

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
