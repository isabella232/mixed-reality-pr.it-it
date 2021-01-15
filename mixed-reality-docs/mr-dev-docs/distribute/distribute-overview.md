---
title: Distribuzione delle app
description: Panoramica delle diverse opzioni di distribuzione per diverse piattaforme e archivi di pubblicazione supportati.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: HoloLens, realtà mista, cuffie immersive, app, UWP, invio, invio, filtri, metadati, requisiti di sistema, parole chiave, predato, certificazione, pacchetto, appx, merchandising
ms.openlocfilehash: b729bd65413587d3ad3b05bef495349b60a6fffd
ms.sourcegitcommit: 47a5c86b4694449c825902631777a9962a40e332
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/14/2021
ms.locfileid: "98215976"
---
# <a name="distributing-your-apps"></a>Distribuzione delle app

![Floaty Bird 3D app lancher in WMR Home](images/distribute-hero-image.png)

La possibilità di ottenere le tue app negli utenti o in tutto il mondo è l'aspetto più importante, a volte accurato, di qualsiasi attività di sviluppo. Il processo è stato semplificato in un set di risorse, che dipendono dallo scenario di distribuzione e distribuzione più adatto per l'utente o il team.

[!INCLUDE[](includes/before-submission.md)]

## <a name="distribution-options"></a>Opzioni di distribuzione

> [!IMPORTANT]
> * Se si condivide l'app con un'altra parte, è necessario compilare e fornire il file appx. 
>     * Se si usa il programma di installazione delle app, è necessario condividere anche il certificato con l'utente.
> 
> * Se si sta condividendo con un'organizzazione, è necessario un account aziendale o dell'Istituto di istruzione e l'accesso all'infrastruttura [MDM (Mobile Device Management)](https://docs.microsoft.com/hololens/hololens-enroll-mdm) per le organizzazioni.  
>    * Se si è l'entità di condivisione, è necessario essere un amministratore nel tenant e usare l'interfaccia di [amministrazione di Microsoft Endpoint Manager](https://docs.microsoft.com/mem/intune/apps/apps-deploy) per rendere disponibile l'app. Un'altra opzione consiste nel condividere il file appx e le dipendenze dell'app con l'utente finale.
>    * Se si è l'utente finale, l'app verrà scaricata automaticamente o sarà disponibile per il download una volta eseguita la registrazione al tenant dell'organizzazione di condivisione. 

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
    <td><strong>Scenario</strong></td>
    <td><strong>Installazioni del dispositivo locale</strong></td>
    <td><strong>Condividi con altri utenti</strong></td>
    <td><strong>Condividere con un'organizzazione</strong></td>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>Programma di installazione app</strong></td>
    <td>✔️</td>
    <td>✔️</td>
    <td>❌</td>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>MDM-Portale aziendale</strong></a></td>
    <td>❌</td>
    <td>❌</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-intune"><strong>MDM-installazione app obbligatoria</strong></a></td>
    <td>❌</td>
    <td>❌</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="submitting-an-app-to-the-microsoft-store.md"><strong>Microsoft Store</strong></a></td>
    <td>❌</td>
    <td>✔️</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-store-business"><strong>Microsoft Store per le aziende</strong></a></td>
    <td>❌</td>
    <td>❌</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-provisioning-package"><strong>Pacchetto di provisioning</strong></a></td>
    <td>✔️</td>
    <td>✔️</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="#other-scenarios"><strong>Distribuzione Win32 personalizzata</strong></a> (non disponibile per i dispositivi HoloLens: vedere di seguito)</td>
    <td>✔️</td>
    <td>✔️</td>
    <td>❌</td>
</tr>
</table>

> [!IMPORTANT]
> Il programma di installazione dell'app non è attualmente disponibile per i dispositivi gestiti o HoloLens (1a generazione).

## <a name="other-scenarios"></a>Altri scenari

* È possibile generare una Win32. File EXE che usa la destinazione di compilazione autonoma del PC da Unity per la distribuzione di applicazioni Win32, inclusi il gioco di Steam e il pass. Una volta ottenuto il. EXE, è possibile inviare le app come di consueto alla piattaforma scelta. 

* Se è necessario installare un'applicazione HoloLens 2 mentre si è offline, fare riferimento alle istruzioni [Secure HoloLens 2 offline](https://docs.microsoft.com/hololens/hololens-common-scenarios-offline-secure) oppure installare l'app tramite un pacchetto di provisioning senza abilitare la modalità sviluppatore.

* È anche possibile distribuire le compilazioni nel dispositivo e condividerle con altri sviluppatori che hanno la modalità di sviluppo abilitata tramite la [distribuzione e il debug con Visual Studio](../develop/platform-capabilities-and-apis/using-visual-studio.md) o l' [installazione di un pacchetto dell'applicazione con il portale del dispositivo](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#sideloading-applications).

## <a name="see-also"></a>Vedere anche
* [Ricerca, installazione e disinstallazione delle applicazioni dal Microsoft Store](https://docs.microsoft.com/hololens/holographic-store-apps)

