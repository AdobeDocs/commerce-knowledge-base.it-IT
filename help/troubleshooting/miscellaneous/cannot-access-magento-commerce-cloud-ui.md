---
title: Impossibile accedere all’interfaccia utente di Adobe Commerce sull’infrastruttura cloud
description: Questo articolo fornisce soluzioni per il problema che impedisce l’accesso all’interfaccia utente di Adobe Commerce on Cloud Infrastructure e causa il messaggio "Errore 403".
exl-id: 948e4acd-abd6-4562-b9c0-771a977188ba
feature: Cloud, Paas
role: Developer
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---

# Impossibile accedere all’interfaccia utente di Adobe Commerce sull’infrastruttura cloud

Questo articolo fornisce soluzioni per il problema per cui non è possibile accedere all&#39;interfaccia utente di Adobe Commerce on Cloud Infrastructure e ricevere l&#39;*errore 403*.

## Problema

Quando tenti di accedere all&#39;interfaccia utente di Adobe Commerce on Cloud Infrastructure per la prima volta, viene visualizzato l&#39;errore *403: Accesso all&#39;ambiente negato*. Questo errore potrebbe verificarsi perché andando all’URL cloud per la prima volta viene caricato il ramo principale e potresti non avere accesso a tale ramo.

## Soluzione

Se ricevi un errore 403 quando accedi all’URL per la prima volta, assicurati di avere un ruolo nel ramo principale.

1. СContatta il proprietario della licenza o un utente con privilegi avanzati sul progetto e assicurati che ti abbiano fornito l&#39;accesso come **utente a livello di ambiente**, descritto anche in [Progetti cloud > Gestisci utenti da Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=it#manage-users-from-the-cloud-console) nella nostra documentazione per sviluppatori.

   Se disponi solo di un ruolo applicabile in un ramo specifico, dovrai passare all’URL di quel ramo, ad esempio,
   `https://console.adobecommerce.com/<owner-name>/<project-id>/<branch-name>`

   La prossima volta che accedi all’URL principale, per impostazione predefinita verrà utilizzato l’ultimo ambiente visitato.

1. Se non riesci ancora ad accedere, сcontatta il proprietario della licenza o un utente con privilegi avanzati sul progetto e assicurati che ti abbiano fornito l&#39;accesso come **utente a livello di progetto**, come descritto in [Progetti cloud > Aggiungere un utente al progetto](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=it#add-a-user-to-the-project) nella documentazione per gli sviluppatori.
1. Se l&#39;errore persiste, [invia un ticket di supporto](https://experienceleague.adobe.com/it/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket).
