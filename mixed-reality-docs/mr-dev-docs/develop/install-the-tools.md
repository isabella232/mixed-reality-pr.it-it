---
title: Installare gli strumenti
description: Iniziare a usare le versioni più recenti di Unity, Visual Studio e degli strumenti consigliati per lo sviluppo per HoloLens e VR.
author: thetuvix
ms.author: alexturn
ms.date: 09/15/2021
ms.topic: article
ms.localizationpriority: high
keywords: aggiornamento, strumenti, attività iniziali, nozioni di base, unity, visual studio, toolkit, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, installazione, Windows, HoloLens, emulatore, unreal, openxr
ms.openlocfilehash: ff365d7d772410a2cd752072a878c37dae1d9b19
ms.sourcegitcommit: 7dad5bde71d429bb23c72a4074e60b6668a7f091
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2021
ms.locfileid: "127857484"
---
# <a name="install-the-tools"></a>Installare gli strumenti

Acquisisci gli strumenti necessari per creare applicazioni per visori VR immersive di Windows Mixed Reality e Microsoft HoloLens. Non è disponibile un SDK separato per lo sviluppo Windows Mixed Reality. Userai Visual Studio con Windows 10 SDK.

Non disponi di un dispositivo di realtà mista? Puoi installare l'[emulatore di HoloLens](platform-capabilities-and-apis/using-the-hololens-emulator.md) per testare alcune funzionalità delle app di realtà mista senza HoloLens. Puoi anche usare il [simulatore Windows Mixed Reality](platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) per testare le tue app di realtà mista per visori VR immersive.

È consigliabile installare il motore di gioco Unity o Unreal come modo più semplice per iniziare a creare app di realtà mista. Se invece vuoi usare un motore personalizzato, puoi anche creare app in DirectX.

Se si usa Unity, è possibile usare [Mixed Reality Toolkit per](https://github.com/Microsoft/MixedRealityToolkit-Unity)la simulazione di input di Unity per testare vari tipi di interazioni di input, ad esempio il tracciamento manuale e l'input di tracciamento oculare. Per i progetti Unreal, usare il [plug-in UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal) per testare le interazioni di input comuni e le funzionalità dell'esperienza utente.

>[!TIP]
>Contrassegna questa pagina e controllala periodicamente per tenerti aggiornato sulla versione più recente di ogni strumento consigliato per lo sviluppo della realtà mista.

<br>

## <a name="installation-checklist"></a>Elenco di controllo per l'installazione

| Strumento | Note |
|---------|---------|
| ![Logo di Windows](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10** (collegamento per l'installazione manuale)</a><br><br>Installa la versione di Windows 10 più recente in modo che il sistema operativo del PC corrisponda alla piattaforma per cui stai creando applicazioni di realtà mista.  | **Installazione di Windows 10** <br> Puoi installare la versione di Windows 10 più recente tramite Windows Update in Impostazioni oppure creando supporti di installazione, usando il collegamento nella colonna sinistra. <br><br>Vedi le [note sulla versione aggiornate](/windows/mixed-reality/enthusiast-guide/release-notes-october-2018.md) per informazioni sulle funzionalità di realtà mista più recenti disponibili con ogni versione di Windows 10. **Abilita la modalità sviluppatore nel PC** in Impostazioni > Aggiornamento e sicurezza > Per sviluppatori. <br><br> **Nota per computer aziendali e gestiti a livello aziendale**<br>Se il computer è gestito dal reparto IT di un'organizzazione, potrebbe essere necessario contattare il reparto per eseguire l'aggiornamento. <br><br> **Versioni 'N' di Windows**<br> i visori VR immersive di Windows Mixed Reality non sono supportati nelle versioni "N" di Windows. |
| ![Immagine del logo di Visual Studio](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2019 (16.8 o versione successiva)** (collegamento per l'installazione)</a> <br><br>Ambiente di sviluppo integrato con funzionalità complete per Windows e altro ancora. Visual Studio verrà usato per scrivere il codice ed eseguire il debug, i test e la distribuzione. | **Installazione di Visual Studio 2019** <br> Assicurati di installare i carichi di lavoro seguenti: <br><br>*● Sviluppo per desktop con C++*<br>*● Sviluppo per la piattaforma UWP (Universal Windows Platform)*<br>*● Sviluppo di giochi con Unity (**se si prevede di usare Unity**)*<br><br>All'interno del carico di lavoro UWP assicurarsi che siano inclusi **i componenti seguenti per l'installazione:**<br><br>*● Windows 10 SDK versione 10.0.19041.0 o 10.0.18362.0*<br>*● Connettività del dispositivo USB (necessaria per distribuire/eseguire il debug HoloLens tramite USB)*<br>*● C++ (v142) Strumenti della piattaforma Windows universale (obbligatorio quando si usa Unity)*<br><br>**Nota su HoloLens visori per dispositivi Windows Mixed Reality desktop**<br>Se si sviluppano solo applicazioni per visori Windows Mixed Reality desktop o HoloLens (prima generazione), è possibile usare Visual Studio 2017 e usare Windows SDK installato.<br><br>**Problemi noti**<br>esistono alcuni problemi noti relativi al debug di app di realtà mista in Visual Studio 2019 versione 16.0.  Assicurarsi di eseguire l'aggiornamento a **Visual Studio 2019 versione 16.8 o successiva**. |
| ![Logo di Visual Studio](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2172762" target="_blank">**HoloLens 2 Emulator (Windows Holographic, versione 21H1 settembre 2021 Update)** (collegamento di installazione: 10.0.20348.1010)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**Emulatore HoloLens (prima generazione)** (collegamento per l'installazione: 10.0.17763.134)</a> <br><br>L'emulatore facoltativo consente di eseguire applicazioni in un'HoloLens di macchina virtuale senza un HoloLens.<br> <br> | Per [altre informazioni sull'introduzione all'emulatore facoltativo,](../develop/platform-capabilities-and-apis/using-the-hololens-emulator.md) vedere Uso dell HoloLens emulatore.<br> <br> **Il sistema deve supportare Hyper-V** per garantire un'installazione corretta dell'emulatore. Vedi più avanti la sezione relativa ai requisiti di sistema per i dettagli. <br> <br> **Nota sull'emulatore HoloLens (prima generazione)** <br>  Per completare correttamente l'installazione, è necessario Visual Studio 2017. Se si sta installando l'emulatore HoloLens (prima generazione) con Visual Studio 2019, è necessario deselezionare i modelli di Visual Studio e [installarli da Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX). |

## <a name="install-your-engine-of-choice"></a>Installare il motore preferito

Ora che è possibile Windows 10, Visual Studio e Windows 10 SDK, è possibile installare e configurare il motore preferito.

> [!div class="nextstepaction"]
> [Scelta del motore](choosing-an-engine.md)

## <a name="troubleshooting"></a>Risoluzione dei problemi

### <a name="setting-developer-mode-is-grayed-out"></a>Impostazione della modalità sviluppatore disabilitata

Se si verificano problemi durante l'abilitazione della modalità sviluppatore, il [proprietario del dispositivo](/hololens/security-adminless-os) potrebbe essere un'altra persona. In modalità multiutente la persona che usa per prima il dispositivo ne è anche il proprietario. Tutti gli utenti successivi non avranno le autorizzazioni necessarie per abilitare la modalità sviluppatore o per eseguire altre modifiche di configurazione. Esiste tuttavia un'eccezione, in base alla quale il primo utente può non essere il proprietario del dispositivo in un ambiente Autopilot, come descritto in dettaglio nella [documentazione relativa alla sicurezza di HoloLens](/hololens/security-adminless-os#device-owner).

Tra le possibili soluzioni vi sono le seguenti:

* Fare abilitare la modalità sviluppatore dal proprietario del dispositivo prima che il dispositivo venga passato ad altri utenti o sviluppatori
* Suggerire all'amministratore IT/MDM di abilitare il [criterio ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) del CSP per il dispositivo specifico o per un gruppo di dispositivi dello sviluppatore.
    * Questo criterio può essere impostato tramite [pacchetti di provisioning](/hololens/hololens-provisioning) o tramite [MDM per i dispositivi HoloLens](/hololens/hololens-mdm-configure)
* Usare [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)

> [!NOTE]
> Per altre informazioni sulla gestione dei dispositivi, vedere la panoramica sulla **[gestione dei dispositivi HoloLens](/hololens/hololens-csp-policy-overview)** .

#### <a name="i-cant-deploy-over-usb"></a>Impossibile distribuire tramite USB

Se non si riesce a distribuire un'applicazione direttamente tramite USB, verificare che siano soddisfatti tutti i requisiti di installazione sopra elencati e seguire l'[esercitazione dettagliata](unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2).
