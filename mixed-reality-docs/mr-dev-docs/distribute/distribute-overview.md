---
title: Distribuzione delle app
description: Panoramica delle diverse opzioni di distribuzione per varie piattaforme e archivi di pubblicazione supportati.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: HoloLens, Realtà mista, visori immersivi, app, uwp, invio, invio, filtri, metadati, requisiti di sistema, parole chiave, wack, certificazione, pacchetto, appx, distribuzione di prodotti
ms.openlocfilehash: 7d4fbc1a7a5767ad8276017c7cdc38e9bb436bc83b12a4d8caeb9a8d84f1caca
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198787"
---
# <a name="distributing-your-apps"></a>Distribuzione delle app

![Floaty bird 3D app lancher in WMR home](images/distribute-hero-image.png)

L'introduzione delle app nelle mani degli utenti o nel mondo è la parte più importante e talvolta scrutante di qualsiasi attività di sviluppo. Il processo è stato semplificato in un set di risorse, che dipendono dagli scenari di distribuzione e distribuzione più adatti all'utente o al team.

[!INCLUDE[](includes/before-submission.md)]

## <a name="distribution-options"></a>Opzioni di distribuzione

> [!IMPORTANT]
> * Se si condivide l'app con un'altra parte, è necessario compilare e fornire il file appx. 
>     * Se si usa Programma di installazione app, è anche necessario condividere il certificato con l'utente.
> 
> * Se si condivide con un'organizzazione, è necessario un account aziendale o dell'istituto di istruzione e l'accesso all'infrastruttura [MDM (Mobile Device Management)](/hololens/hololens-enroll-mdm) dell'organizzazione.  
>    * Se si è l'entità di condivisione, è necessario essere un amministratore nel tenant e usare l'interfaccia Microsoft Endpoint Manager [di amministrazione](/mem/intune/apps/apps-deploy) per rendere disponibile l'app. Un'altra opzione è condividere il file appx e le dipendenze dell'app con l'utente finale.
>    * Se si è l'utente finale, l'app verrà scaricata automaticamente o sarà disponibile per il download dopo la registrazione nel tenant dell'organizzazione di condivisione. 

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
    <td><strong>Scenario</strong></td>
    <td><strong>Installazioni di dispositivi locali</strong></td>
    <td><strong>Condividere con chiunque</strong></td>
    <td><strong>Condividere con un'organizzazione</strong></td>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>Programma di installazione app</strong></td>
    <td>✔️</td>
    <td>✔️</td>
    <td>❌</td>
</tr>
<tr>
    <td><a href="/hololens/app-deploy-app-installer"><strong>MDM - Portale aziendale</strong></a></td>
    <td>❌</td>
    <td>❌</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="/hololens/app-deploy-intune"><strong>MDM - Installazione dell'app richiesta</strong></a></td>
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
    <td><a href="/hololens/app-deploy-store-business"><strong>Microsoft Store per le aziende</strong></a></td>
    <td>❌</td>
    <td>❌</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="/hololens/app-deploy-provisioning-package"><strong>Pacchetto di provisioning</strong></a></td>
    <td>✔️</td>
    <td>✔️</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="#other-scenarios"><strong>Distribuzione Win32 personalizzata</strong></a> (non disponibile per HoloLens dispositivi - vedere di seguito)</td>
    <td>✔️</td>
    <td>✔️</td>
    <td>❌</td>
</tr>
</table>

> [!IMPORTANT]
> Programma di installazione app non è attualmente disponibile per i dispositivi gestiti o HoloLens (prima generazione).

## <a name="other-scenarios"></a>Altri scenari

* È possibile produrre un file .EXE Win32 usando la destinazione di compilazione autonoma del PC da Unity per la distribuzione di applicazioni Win32, tra cui Steam e Game Pass. Dopo aver creato il .EXE, è possibile inviare le app come di consueto alla piattaforma scelta. 

* Se è necessario installare un'applicazione HoloLens 2 mentre si è offline, fare riferimento alle istruzioni di sicurezza [offline](/hololens/hololens-common-scenarios-offline-secure) HoloLens 2 o installare l'app tramite un pacchetto di provisioning senza abilitare la modalità sviluppatore.

* È anche possibile distribuire compilazioni nel dispositivo e condividerle con altri sviluppatori con la modalità sviluppatore abilitata distribuendo e debug con [Visual Studio](../develop/platform-capabilities-and-apis/using-visual-studio.md) o installando un pacchetto dell'applicazione con [l'Portale di dispositivi](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#sideloading-applications).

## <a name="see-also"></a>Vedi anche
* [Ricerca, installazione e disinstallazione di applicazioni dal Microsoft Store](/hololens/holographic-store-apps)