---
title: Panoramica dello sviluppo nativo
description: Creare un motore di realtà mista basato su DirectX usando direttamente le API di realtà mista di Windows.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: DirectX, rendering olografico, nativo, app nativa, WinRT, app WinRT, API della piattaforma, motore personalizzato, middleware
ms.openlocfilehash: fb51dfe15de26b80db255f0daca69e913f9ad35c
ms.sourcegitcommit: c199872c11adae7de24929ed043ea90dea087b3e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903110"
---
# <a name="native-development-overview"></a>Panoramica dello sviluppo nativo

![Logo banner nativo](../images/native_logo_banner.png)

i motori 3D come [Unity](../unity/unity-development-overview.md) o [Unreal](../unreal/unreal-development-overview.md) non sono gli unici percorsi di sviluppo di realtà mista aperti. È anche possibile creare app per realtà mista codificando direttamente le API per la realtà mista di Windows con DirectX 11 o DirectX 12. Sfruttando la piattaforma direttamente, si crea essenzialmente un middleware o un Framework personalizzato. 

> [!IMPORTANT]
> Se si vuole mantenere un progetto WinRT esistente, passare alla documentazione principale di [WinRT](creating-a-holographic-directx-project.md). 

## <a name="development-checkpoints"></a>Checkpoint di sviluppo

Usare i checkpoint seguenti per trasferire i giochi e le applicazioni di Unity nel mondo della realtà mista.

### <a name="1-getting-started"></a>1. Guida introduttiva

La realtà mista [di Windows supporta due tipi di app](../../design/app-views.md):
* **Applicazioni a realtà mista** (UWP o Win32) che usano l'API [HOLOGRAPHICSPACE](getting-a-holographicspace.md) o l' [API OpenXR](openxr.md) per eseguire il rendering di una [visualizzazione immersiva](../../design/app-views.md) per l'utente che riempie la visualizzazione dell'auricolare
* **app 2D** (UWP) che usano DirectX, XAML o un altro Framework per eseguire il rendering di [visualizzazioni 2D](../../design/app-views.md#2d-views) in slate nella Home realtà mista di Windows

Le differenze tra lo sviluppo di DirectX per le [visualizzazioni 2D e le visualizzazioni immersive](../../design/app-views.md) riguardano principalmente il rendering olografico e l'input spaziale. Il [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) dell'applicazione UWP o l'HWND dell'applicazione Win32 sono obbligatori e rimangono in gran parte uguali. Lo stesso vale per le API WinRT disponibili per l'app. È tuttavia necessario usare un subset diverso di queste API per sfruttare le funzionalità olografiche. Ad esempio, presentazione catena e frame presenti vengono gestiti dal sistema per le applicazioni olografiche allo scopo di abilitare un ciclo di frame stimato per la posa.

[!INCLUDE[](../includes/native-getting-started.md)]

### <a name="2-core-building-blocks"></a>2. Componenti fondamentali

Le applicazioni di realtà mista di Windows usano le API seguenti per creare esperienze di [realtà mista](../../discover/mixed-reality.md) per HoloLens e altri auricolari immersivi:

|  Caratteristica  |  Funzionalità  |
| --- | --- |
| [Sguardo fisso](../../design/gaze-and-commit.md) | Consentire agli utenti di puntare agli ologrammi fissandoli con lo sguardo |
| [Movimento](../../design/gaze-and-commit.md#composite-gestures) | Aggiungere azioni spaziali alle app |
| [Rendering olografico](../platform-capabilities-and-apis/rendering.md) | Creare un ologramma in una posizione precisa in tutto il mondo intorno agli utenti |
| [Controller di movimento](../../design/motion-controllers.md) | Consentire agli utenti di intervenire sugli ambienti di realtà mista |
| [Mapping spaziale](../../design/spatial-mapping.md) | Mappare lo spazio fisico con una mesh virtuale sovrapposta per contrassegnare i limiti dell'ambiente |
| [Chiamata vocale](../../design/voice-input.md) | Acquisire parole chiave, frasi e dettature pronunciate degli utenti |
 
> [!NOTE]
> È possibile trovare le funzionalità principali imminenti e in fase di sviluppo nella documentazione di [Roadmap](openxr.md#roadmap) per OpenXR.

### <a name="3-deploying-and-testing"></a>3. distribuzione e test

È possibile sviluppare app usando OpenXR in un visore VR immersive di HoloLens 2 o Windows Mixed Reality sul desktop.  Se non si ha accesso a una cuffia, è invece possibile usare l' [emulatore HoloLens 2](../platform-capabilities-and-apis/using-the-hololens-emulator.md) o il [simulatore di realtà mista di Windows](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) .

## <a name="whats-next"></a>Passaggi successivi

Il lavoro degli sviluppatori non finisce mai, soprattutto per quanto riguarda la conoscenza di nuovi strumenti o SDK. Le sezioni seguenti consentono di affrontare aspetti più avanzati rispetto al materiale di livello principiante già completato e di accedere a risorse utili se si rimane bloccati. Questi argomenti e queste risorse non sono presentati in ordine sequenziale, quindi possono essere esplorati liberamente.

### <a name="additional-resources"></a>Risorse aggiuntive

Se si sta cercando di livellare il gioco OpenXR, vedere i collegamenti seguenti:

* [Procedure consigliate per OpenXR](openxr-best-practices.md)
* [Prestazioni di OpenXR](openxr-performance.md)
* [Risoluzione dei problemi di OpenXR](openxr-troubleshooting.md)

## <a name="see-also"></a>Vedere anche
* [Modello di app](../../design/app-model.md)
* [Visualizzazioni delle app](../../design/app-views.md)
