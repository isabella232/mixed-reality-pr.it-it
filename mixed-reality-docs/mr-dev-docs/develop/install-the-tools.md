---
title: Installare gli strumenti
description: Inizia da qui per prepararti allo sviluppo della realtà mista. Questo articolo deve sempre essere aggiornato con le versioni più recenti di Unity, Visual Studio e altri strumenti consigliati per lo sviluppo con visori VR immersivi Windows Mixed Reality e HoloLens.
author: thetuvix
ms.author: alexturn
ms.date: 09/07/2020
ms.topic: article
ms.localizationpriority: high
keywords: aggiornamento, strumenti, attività iniziali, nozioni di base, unity, visual studio, toolkit, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, installazione, Windows, HoloLens, emulatore, unreal, openxr
ms.openlocfilehash: 5a5690b94da1d191c2dde0a6550a0d84800bf7ea
ms.sourcegitcommit: db77eb511b2b8afc5858515f34b3edffb33d034b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2020
ms.locfileid: "96755474"
---
# <a name="install-the-tools"></a>Installare gli strumenti

Acquisisci gli strumenti necessari per creare applicazioni per visori VR immersive di Windows Mixed Reality e Microsoft HoloLens. Non è disponibile un SDK separato per lo sviluppo Windows Mixed Reality. Userai Visual Studio con Windows 10 SDK.

Non disponi di un dispositivo di realtà mista? Puoi installare l'[emulatore di HoloLens](platform-capabilities-and-apis/using-the-hololens-emulator.md) per testare alcune funzionalità delle app di realtà mista senza HoloLens. Puoi anche usare il [simulatore Windows Mixed Reality](platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) per testare le tue app di realtà mista per visori VR immersive. Se si usa Unity, è possibile usare la simulazione di input di [Mixed Reality Toolkit (MRTK)](https://github.com/Microsoft/MixedRealityToolkit-Unity) per testare vari tipi di interazioni di input, ad esempio attraverso il tracciamento della mano e il tracciamento oculare.

Il modo più semplice per iniziare a creare app di realtà mista consiste nell'installare il motore di gioco Unity. Se invece vuoi usare un motore personalizzato, puoi anche creare app in DirectX.

>[!TIP]
>Contrassegna questa pagina e controllala periodicamente per tenerti aggiornato sulla versione più recente di ogni strumento consigliato per lo sviluppo della realtà mista.

<br>

## <a name="installation-checklist"></a>Elenco di controllo per l'installazione


| Strumento | Note |
|---------|---------|
| ![Logo di Windows](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10** (collegamento per l'installazione manuale)</a><br><br>Installa la versione di Windows 10 più recente in modo che il sistema operativo del PC corrisponda alla piattaforma per cui stai creando applicazioni di realtà mista.  | **Installazione di Windows 10** <br> Puoi installare la versione di Windows 10 più recente tramite Windows Update in Impostazioni oppure creando supporti di installazione, usando il collegamento nella colonna sinistra. <br><br>Vedi le [note sulla versione aggiornate](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-october-2018.md) per informazioni sulle funzionalità di realtà mista più recenti disponibili con ogni versione di Windows 10. **Abilita la modalità sviluppatore nel PC** in Impostazioni > Aggiornamento e sicurezza > Per sviluppatori. <br><br> **Nota per computer aziendali e gestiti a livello aziendale**<br>Se il computer è gestito dal reparto IT di un'organizzazione, potrebbe essere necessario contattare il reparto per eseguire l'aggiornamento. <br><br> **Versioni 'N' di Windows**<br> i visori VR immersive di Windows Mixed Reality non sono supportati nelle versioni "N" di Windows. |
| ![Immagine del logo di Visual Studio](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2019 (16.8 o versione successiva)** (collegamento per l'installazione)</a> <br><br>Ambiente di sviluppo integrato con funzionalità complete per Windows e altro ancora. Visual Studio verrà usato per scrivere il codice ed eseguire il debug, i test e la distribuzione. | **Installazione di Visual Studio 2019** <br> Assicurati di installare i carichi di lavoro seguenti: <br><br>*● Sviluppo per desktop con C++*<br>*● Sviluppo per la piattaforma UWP (Universal Windows Platform)*<br><br>Nel carico di lavoro della piattaforma UWP assicurati di selezionare il componente facoltativo seguente se prevedi di sviluppare per HoloLens:<br><br>*● Connettività dispositivi USB*<br><br>**Nota su Unity**<br>a meno che non si stia intenzionalmente tentando di installare una versione più recente (non LTS) di Unity per uno scopo specifico, è consigliabile *non* installare il carico di lavoro Unity come parte dell'installazione di Visual Studio e installare invece il flusso **Unity 2019 LTS** come indicato di seguito.<br><br>**Problemi noti**<br>esistono alcuni problemi noti relativi al debug di app di realtà mista in Visual Studio 2019 versione 16.0.  Assicurarsi di eseguire l'aggiornamento a **Visual Studio 2019 versione 16.8 o successiva**. |
| ![Logo di Windows](images/Windows10_logo.png)<br><br><a href="https://developer.microsoft.com//windows/downloads/windows-10-sdk" target="_blank">**Windows 10 SDK (10.0.18362.0)** (collegamento per l'installazione manuale)</a> <br><br>Include le intestazioni, le librerie, i metadati e gli strumenti più recenti per la creazione di app di Windows 10 in HoloLens 2. | **Per creare app HoloLens 2, è necessario installare Windows SDK, build 18362 o versioni successive.**<br> <br> Se sviluppi solo applicazioni per visori VR di Windows Mixed Reality desktop o per HoloLens (prima generazione), puoi usare Windows SDK installato da Visual Studio 2017. |
| ![Logo di Visual Studio](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2145829" target="_blank">**Emulatore HoloLens 2 (Windows Holographic, versione 2004, aggiornamento di ottobre 2020)** (collegamento di installazione: 10.0.19041.1124)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**Emulatore HoloLens (prima generazione)** (collegamento per l'installazione: 10.0.17763.134)</a> <br><br>L'emulatore permette di eseguire le applicazioni in un'immagine di macchina virtuale HoloLens senza un dispositivo HoloLens fisico.<br> <br> | Vedi [Uso dell'emulatore di HoloLens](../develop/platform-capabilities-and-apis/using-the-hololens-emulator.md) per altre informazioni su come iniziare a usare l'emulatore.<br> <br> **Il sistema deve supportare Hyper-V** per garantire un'installazione corretta dell'emulatore. Vedi più avanti la sezione relativa ai requisiti di sistema per i dettagli. <br> <br> **Nota sull'emulatore HoloLens (prima generazione)** <br>  Per completare correttamente l'installazione, è necessario Visual Studio 2017. Se si sta installando l'emulatore HoloLens (prima generazione) con Visual Studio 2019, è necessario deselezionare i modelli di Visual Studio e [installarli da Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX). |

## <a name="choose-your-engine"></a>Scegli il motore

Dopo aver predisposto Windows 10, Visual Studio e Windows 10 SDK, è possibile scegliere un motore per la compilazione.

[!INCLUDE[](includes/tools-overview.md)]

