---
title: Installare gli strumenti
description: Iniziare a usare le versioni più recenti di Unity, Visual Studio e degli strumenti consigliati per lo sviluppo per HoloLens e VR.
author: thetuvix
ms.author: alexturn
ms.date: 05/11/2021
ms.topic: article
ms.localizationpriority: high
keywords: aggiornamento, strumenti, attività iniziali, nozioni di base, unity, visual studio, toolkit, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, installazione, Windows, HoloLens, emulatore, unreal, openxr
ms.openlocfilehash: 3cb1550dc70689ed098f9c7fb666385af51fa73d
ms.sourcegitcommit: cf1c1a7cb67c850c61d3907a2519b51cd890a392
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2021
ms.locfileid: "112022813"
---
# <a name="install-the-tools"></a>Installare gli strumenti

Acquisisci gli strumenti necessari per creare applicazioni per visori VR immersive di Windows Mixed Reality e Microsoft HoloLens. Non è disponibile un SDK separato per lo sviluppo Windows Mixed Reality. Userai Visual Studio con Windows 10 SDK.

Non disponi di un dispositivo di realtà mista? Puoi installare l'[emulatore di HoloLens](platform-capabilities-and-apis/using-the-hololens-emulator.md) per testare alcune funzionalità delle app di realtà mista senza HoloLens. Puoi anche usare il [simulatore Windows Mixed Reality](platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) per testare le tue app di realtà mista per visori VR immersive. 

È consigliabile installare il motore di gioco Unity o Unreal come modo più semplice per iniziare a creare app di realtà mista. Se invece vuoi usare un motore personalizzato, puoi anche creare app in DirectX.

Se si usa Unity, è possibile usare [mixed reality toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)per la simulazione di input di Unity per testare vari tipi di interazioni di input, ad esempio il tracciamento manuale e l'input di tracciamento oculare. Per i progetti Unreal, usare il [plug-in UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal) per testare le interazioni di input comuni e le funzionalità dell'esperienza utente.

>[!TIP]
>Contrassegna questa pagina e controllala periodicamente per tenerti aggiornato sulla versione più recente di ogni strumento consigliato per lo sviluppo della realtà mista.

<br>

## <a name="installation-checklist"></a>Elenco di controllo per l'installazione

| Strumento | Note |
|---------|---------|
| ![Logo di Windows](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10** (collegamento per l'installazione manuale)</a><br><br>Installa la versione di Windows 10 più recente in modo che il sistema operativo del PC corrisponda alla piattaforma per cui stai creando applicazioni di realtà mista.  | **Installazione di Windows 10** <br> Puoi installare la versione di Windows 10 più recente tramite Windows Update in Impostazioni oppure creando supporti di installazione, usando il collegamento nella colonna sinistra. <br><br>Vedi le [note sulla versione aggiornate](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-october-2018.md) per informazioni sulle funzionalità di realtà mista più recenti disponibili con ogni versione di Windows 10. **Abilita la modalità sviluppatore nel PC** in Impostazioni > Aggiornamento e sicurezza > Per sviluppatori. <br><br> **Nota per computer aziendali e gestiti a livello aziendale**<br>Se il computer è gestito dal reparto IT di un'organizzazione, potrebbe essere necessario contattare il reparto per eseguire l'aggiornamento. <br><br> **Versioni 'N' di Windows**<br> i visori VR immersive di Windows Mixed Reality non sono supportati nelle versioni "N" di Windows. |
| ![Immagine del logo di Visual Studio](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2019 (16.8 o versione successiva)** (collegamento per l'installazione)</a> <br><br>Ambiente di sviluppo integrato con funzionalità complete per Windows e altro ancora. Visual Studio verrà usato per scrivere il codice ed eseguire il debug, i test e la distribuzione. | **Installazione di Visual Studio 2019** <br> Assicurati di installare i carichi di lavoro seguenti: <br><br>*● Sviluppo per desktop con C++*<br>*● Sviluppo per la piattaforma UWP (Universal Windows Platform)*<br>*● Sviluppo di giochi con Unity (**se si prevede di usare Unity**)*<br><br>All'interno del carico di lavoro UWP assicurarsi che siano inclusi **i componenti seguenti per l'installazione:**<br><br>*● Windows 10 SDK versione 10.0.19041.0 o 10.0.18362.0*<br>*● Connettività del dispositivo USB (necessaria per distribuire/eseguire il debug in HoloLens tramite USB)*<br>*● C++ (v142) piattaforma UWP (Universal Windows Platform) strumenti (obbligatori quando si usa Unity)*<br><br>**Nota su HoloLens (prima generazione) e sui visori Windows Mixed Reality desktop**<br>Se si sviluppano solo applicazioni per visori Windows Mixed Reality desktop o HoloLens (prima generazione), è possibile usare Visual Studio 2017 e usare il Windows SDK installato.<br><br>**Problemi noti**<br>esistono alcuni problemi noti relativi al debug di app di realtà mista in Visual Studio 2019 versione 16.0.  Assicurarsi di eseguire l'aggiornamento a **Visual Studio 2019 versione 16.8 o successiva**. |
| ![Logo di Visual Studio](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2165258" target="_blank">**HoloLens 2 Emulator (Windows Holographic, versione 21H1 aggiornamento di giugno 2021)** (collegamento di installazione: 10.0.20348.1007)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**Emulatore HoloLens (prima generazione)** (collegamento per l'installazione: 10.0.17763.134)</a> <br><br>L'emulatore facoltativo consente di eseguire applicazioni in un'immagine di macchina virtuale HoloLens senza un dispositivo HoloLens fisico.<br> <br> | Per [altre informazioni sull'introduzione all'emulatore](../develop/platform-capabilities-and-apis/using-the-hololens-emulator.md) facoltativo, vedere Uso dell'emulatore HoloLens.<br> <br> **Il sistema deve supportare Hyper-V** per garantire un'installazione corretta dell'emulatore. Vedi più avanti la sezione relativa ai requisiti di sistema per i dettagli. <br> <br> **Nota sull'emulatore HoloLens (prima generazione)** <br>  Per completare correttamente l'installazione, è necessario Visual Studio 2017. Se si sta installando l'emulatore HoloLens (prima generazione) con Visual Studio 2019, è necessario deselezionare i modelli di Visual Studio e [installarli da Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX). |

## <a name="install-your-engine-of-choice"></a>Installare il motore preferito

Ora che è possibile Windows 10, Visual Studio e Windows 10 SDK, è possibile installare e configurare il motore preferito. 

Se è ancora necessario scegliere un motore, vedere Introduzione [allo sviluppo di realtà mista](./development.md?tabs=unity#what-technology-path-are-you-interested-in). 

[!INCLUDE[](includes/tools-overview.md)]