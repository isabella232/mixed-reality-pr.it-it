---
title: Panoramica dello sviluppo nativo
description: Informazioni su come creare un motore di realtà mista basato su DirectX usando direttamente Windows Mixed Reality API.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: DirectX, rendering olografico, app nativa, nativa, WinRT, app WinRT, API della piattaforma, motore personalizzato, middleware, visore VR di realtà mista, visore VR di realtà mista windows, visore VR di realtà virtuale
ms.openlocfilehash: 056cb0c07002cb319e8acadf66e7f59650f5e00413440d6ad0103aa8ee936400
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200169"
---
# <a name="native-development-overview"></a>Panoramica dello sviluppo nativo

![Logo del banner nativo](../images/native_logo_banner.png)

I motori 3D come [Unity](../unity/unity-development-overview.md) o [Unreal](../unreal/unreal-development-overview.md) non sono gli unici percorsi di sviluppo di realtà mista aperti. È anche possibile creare app di realtà mista usando le API Windows Mixed Reality con DirectX 11 o DirectX 12. Nell'origine della piattaforma si sta essenzialmente creando il proprio middleware o framework. 

> [!IMPORTANT]
> Se hai un progetto WinRT esistente che vuoi gestire, vai alla documentazione [principale di WinRT.](creating-a-holographic-directx-project.md) 

## <a name="development-checkpoints"></a>Checkpoint di sviluppo

Usare i checkpoint seguenti per trasferire i giochi e le applicazioni di Unity nel mondo della realtà mista.

### <a name="1-getting-started"></a>1. Guida introduttiva

Windows Mixed Reality supporta due [tipi di app:](../../design/app-views.md)
* Applicazioni UWP o Win32 **Mixed Reality** che usano l'API [HolographicSpace](getting-a-holographicspace.md) o [OpenXR](openxr.md) per eseguire il rendering di una visualizzazione [immersiva](../../design/app-views.md) che riempie lo schermo del visore VR
* **App 2D** (UWP) che usano DirectX, XAML o un altro framework per eseguire il rendering delle visualizzazioni [2D](../../design/app-views.md#2d-views) negli slate nella home page Windows Mixed Reality

Le differenze tra lo sviluppo DirectX per le [visualizzazioni 2D](../../design/app-views.md) e le visualizzazioni immersive riguardano principalmente il rendering olografico e l'input spaziale. [IFrameworkView](/uwp/api/Windows.ApplicationModel.Core.IFrameworkView) dell'applicazione UWP o HWND dell'applicazione Win32 sono necessari e rimangono in gran parte uguali. Lo stesso vale per le API WinRT disponibili per l'app. Tuttavia, è necessario usare un subset diverso di queste API per sfruttare le funzionalità olografiche. Ad esempio, il sistema per le applicazioni olografiche gestisce lo swapchain e il fotogramma presenti per abilitare un ciclo di fotogrammi con previsione della posizione.

[!INCLUDE[](../includes/native-getting-started.md)]

### <a name="2-core-building-blocks"></a>2. Componenti fondamentali

Windows Mixed Reality applicazioni usano le API seguenti per creare esperienze di [realtà](../../discover/mixed-reality.md) mista per HoloLens e altri visori VR immersive:

|  Caratteristica  |  Funzionalità  |
| --- | --- |
| [Sguardo fisso](../../design/gaze-and-commit.md) | Consentire agli utenti di puntare agli ologrammi fissandoli con lo sguardo |
| [Movimento](../../design/gaze-and-commit.md#composite-gestures) | Aggiungere azioni spaziali alle app |
| [Rendering olografico](../platform-capabilities-and-apis/rendering.md) | Disegnare un ologramma in una posizione precisa nel mondo intorno agli utenti |
| [Controller del movimento](../../design/motion-controllers.md) | Consenti agli utenti di intervenire negli ambienti di realtà mista |
| [Mapping spaziale](../../design/spatial-mapping.md) | Mappare lo spazio fisico con una mesh virtuale sovrapposta per contrassegnare i limiti dell'ambiente |
| [Chiamata vocale](../../design/voice-input.md) | Acquisire parole chiave, frasi e dettature pronunciate degli utenti |
 
> [!NOTE]
> È possibile trovare funzionalità di base imminenti e in fase di sviluppo nella documentazione della [roadmap](openxr.md#roadmap) di OpenXR.

### <a name="3-deploying-and-testing"></a>3. Distribuzione e test

È possibile sviluppare in un desktop usando OpenXR in un dispositivo HoloLens 2 o Windows Mixed Reality visore VR immersive.  Se non si ha accesso a un visore VR, è [possibile](../platform-capabilities-and-apis/using-the-hololens-emulator.md) usare il HoloLens 2 Emulator o il [simulatore Windows Mixed Reality](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) dispositivo.

## <a name="whats-next"></a>Passaggi successivi

Il lavoro di uno sviluppatore non finisce mai, soprattutto per quanto riguarda l'apprendimento di nuovi strumenti o SDK. Le sezioni seguenti illustrano le aree oltre il materiale di livello principiante già completato. Questi argomenti e risorse non sono in ordine sequenziale, quindi è possibile passare da un'esplorazione all'altra.

### <a name="additional-resources"></a>Risorse aggiuntive

Se si sta cercando di livellare il gioco OpenXR, vedere i collegamenti seguenti:

* [Procedure consigliate per OpenXR](openxr-best-practices.md)
* [Prestazioni di OpenXR](openxr-performance.md)
* [Risoluzione dei problemi di OpenXR](openxr-troubleshooting.md)

## <a name="see-also"></a>Vedi anche
* [Modello di app](../../design/app-model.md)
* [Visualizzazioni delle app](../../design/app-views.md)