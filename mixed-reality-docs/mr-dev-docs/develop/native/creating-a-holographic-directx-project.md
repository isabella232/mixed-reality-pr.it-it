---
title: Creazione di un progetto DirectX olografico
description: Informazioni su come creare una nuova app DirectX olografica basata sul modello Windows Mixed Reality app.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality, app olografica, nuova app, app UWP, app modello, ologrammi, nuovo progetto, procedura dettagliata, download, codice di esempio, visore per la realtà mista, visore windows mixed reality, visore per la realtà virtuale
ms.openlocfilehash: 7de7d73ec1e5fd8abde6d4822c86628e090fdf0cf89769fc9ef21311ff1aff15
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200174"
---
# <a name="creating-a-holographic-directx-project"></a>Creazione di un progetto DirectX olografico

> [!NOTE]
> Questo articolo è correlato alle API native WinRT legacy.  Per i nuovi progetti di app native, è consigliabile usare **[l'API OpenXR](openxr-getting-started.md)**.

Un'app olografica creata per un HoloLens sarà <a href="/windows/uwp/get-started/universal-application-platform-guide" target="_blank">un'app UWP (Universal Windows Platform).</a>  Se la destinazione è Windows Mixed Reality visori, è possibile creare un'app UWP o un'app Win32.

Il modello di app UWP olografica DirectX 11 è molto simile al modello di app UWP DirectX 11. Il modello include un ciclo di programma, una **classe DeviceResources** per gestire il contesto e il dispositivo Direct3D e una classe renderer di contenuto semplificata. Ha anche un <a href="/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView,</a>proprio come qualsiasi altra app UWP.

L'app di realtà mista, tuttavia, include alcune funzionalità aggiuntive che non sono presenti in una tipica app UWP Direct3D. Il modello Windows Mixed Reality'app può:
* Gestire le risorse del dispositivo Direct3D associate alle fotocamere olografiche.
* Recuperare i buffer indietro della fotocamera dal sistema. Nel caso di Direct3D12, creare risorse del buffer nascosto olografico e gestire la durata delle risorse.
* Gestire [l'input](../../design/gaze-and-commit.md) dello sguardo e riconoscere un [movimento](../../design/gaze-and-commit.md#composite-gestures).
* Passare alla modalità di rendering stereo a schermo intero.

## <a name="how-do-i-get-started"></a>Come iniziare?

Installare [prima gli strumenti](../install-the-tools.md)seguendo le istruzioni per il download Visual Studio 2019 e i modelli di app Windows Mixed Reality app. I modelli di app di realtà mista sono disponibili nel marketplace Visual Studio come [download Web](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX)o installandoli come estensione tramite l'interfaccia Visual Studio interfaccia utente.

A questo punto è possibile creare l'app DirectX 11 Windows Mixed Reality! Si noti che per rimuovere il contenuto di esempio, impostare come commento **DRAW_SAMPLE_CONTENT** direttiva del preprocessore in *pch.h*.

## <a name="creating-a-uwp-project"></a>Creazione di un progetto UWP

Dopo l'installazione degli strumenti,](.. /install-the-tools.md) è quindi possibile creare un progetto UWP DirectX olografico.

Per creare un nuovo progetto in Visual Studio 2019:
1. Avviare **Visual Studio**.
2. Nella sezione **Informazioni di base** a destra selezionare **Crea un nuovo progetto**.
3. Nei menu a discesa della  finestra di dialogo Crea un nuovo progetto selezionare **C++**, **Windows Mixed Reality** e **UWP**.
4. Selezionare **Holographic DirectX 11 App (Universal Windows) (C++/WinRT).**
   ![Screenshot del modello di progetto di app UWP Holographic DirectX 11 C++/WinRT in Visual Studio 2019](images/holographic-directx-app-cpp-new-project-2019.png)<br>
   *Modello di progetto di app UWP Holographic DirectX 11 C++/WinRT in Visual Studio 2019*
   >[!IMPORTANT]
   >Assicurarsi che il nome del modello di progetto includa "(C++/WinRT)".  In caso contrario, è installata una versione precedente dei modelli di progetto olografici.  Per ottenere i modelli di progetto più recenti, [installarli](../install-the-tools.md) come estensione per Visual Studio 2019.
5. Selezionare **Avanti**.
5. Compilare le **caselle Project nome** e **Posizione** e selezionare o toccare **Crea**. Viene creato il progetto di app olografica.
6. Per lo sviluppo con destinazione HoloLens 2,  assicurarsi  che la versione di destinazione e la versione minima siano impostate su **Windows 10 versione 1903.**  Se si ha come destinazione anche HoloLens visori per dispositivi Windows Mixed Reality desktop, è  possibile impostare Versione minima su **Windows 10, versione 1809**. Ciò richiederà alcuni <a href="/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">controlli adattivi della</a> versione nel codice quando si usano nuove funzionalità di HoloLens 2.
   ![Screenshot dell'impostazione Windows 10 versione 1903 come versione minima e di destinazione](images/new-uwp-project.png)<br>
   *Impostazione **Windows 10 versione 1903** come versione di destinazione e minima*
   >[!IMPORTANT]
   >Se l'opzione Windows 10, versione **1903,** non è installata la versione Windows 10 SDK più recente.  Per visualizzare questa opzione, installare la versione <a href="https://developer.microsoft.com/windows/downloads/windows-10-sdk" target="_blank">10.0.18362.0</a>o successiva di Windows 10 SDK .

Per creare un nuovo progetto in Visual Studio 2017:
1. Avviare **Visual Studio**.
2. Scegliere **Nuovo** dal menu  File e selezionare Project **dal** menu di scelta rapida. Verrà visualizzata la finestra di dialogo **Nuovo progetto**.
3. Espandere **Installato** a sinistra ed espandere il **nodo Visual C++** lingua.
4. Passare al nodo **Windows Universal > Holographic** e selezionare **Holographic DirectX 11 App (Universal Windows) (C++/WinRT).**
   ![Screenshot del modello di progetto di app UWP Holographic DirectX 11 C++/WinRT in Visual Studio 2017](images/holographic-directx-app-cpp-new-project.png)<br>
   *Modello di progetto di app UWP Holographic DirectX 11 C++/WinRT in Visual Studio 2017*
   >[!IMPORTANT]
   >Assicurarsi che il nome del modello di progetto includa "(C++/WinRT)".  In caso contrario, è installata una versione precedente dei modelli di progetto olografici.  Per ottenere i modelli di progetto più recenti, [installarli](../install-the-tools.md) come estensione per Visual Studio 2017.
5. Compilare le **caselle di** **testo Nome** e Posizione e selezionare o toccare **OK.** Viene creato il progetto di app olografica.
6. Per lo sviluppo con destinazione HoloLens 2,  assicurarsi  che la versione di destinazione e la versione minima siano impostate su **Windows 10 versione 1903.**  Se si ha come destinazione anche HoloLens visori per dispositivi Windows Mixed Reality desktop, è  possibile impostare Versione minima su **Windows 10, versione 1809**. Ciò richiederà alcuni <a href="/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">controlli adattivi della</a> versione nel codice quando si usano nuove funzionalità di HoloLens 2.
   ![Screenshot dell'impostazione Windows 10 versione 1903 come versione minima e di destinazione](images/new-uwp-project.png)<br>
   *Impostazione **Windows 10 versione 1903** come versione di destinazione e minima*
   >[!IMPORTANT]
   >Se l'opzione Windows 10, versione **1903,** non è installata la versione Windows 10 SDK più recente.  Per visualizzare questa opzione, installare la versione <a href="https://developer.microsoft.com/windows/downloads/windows-10-sdk" target="_blank">10.0.18362.0</a>o successiva di Windows 10 SDK .

Il modello genera un progetto <a href="/windows/uwp/cpp-and-winrt-apis/" target="_blank">usando C++/WinRT</a>, una proiezione in linguaggio C++17 delle API di runtime di Windows che supporta qualsiasi compilatore C++17 conforme agli standard.  Il progetto illustra come creare un cubo bloccato dal mondo posizionato a 2 metri dall'utente. L'utente [può toccare o](../../design/gaze-and-commit.md#composite-gestures) premere un pulsante sul controller per posizionare il cubo in una posizione diversa specificata dallo sguardo dell'utente. [](../../design/gaze-and-commit.md) È possibile modificare questo progetto per creare qualsiasi app di realtà mista.

È anche possibile creare un nuovo progetto usando il modello di progetto olografico di **Visual C#,** basato su SharpDX.  Se il progetto C# olografico non è stato avviato dal modello di app holographic di Windows, è necessario copiare il file ms.fxcompile.targets da un progetto modello C# Windows Mixed Reality e importarlo nel file con estensione csproj per compilare i file HLSL aggiunti al progetto. Un modello Direct3D 12 viene fornito anche nell'estensione Windows Mixed Reality di modelli di app per Visual Studio.

Per [informazioni su come compilare](../platform-capabilities-and-apis/using-visual-studio.md) e distribuire l'esempio nel HoloLens, nel PC con dispositivo immersivo collegato o in un emulatore, vedere Using Visual Studio to deploy and debug (Uso di Visual Studio per distribuire ed eseguire il debug).

Le altre istruzioni riportate di seguito presuppongono che si sta usando C++ per compilare l'app.

### <a name="uwp-app-entry-point"></a>Punto di ingresso dell'app UWP

L'app UWP olografica viene avviata nella **funzione wWinMain** in AppView.cpp. La **funzione wWinMain** crea <a href="/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">l'oggetto IFrameworkView</a> dell'app e avvia <a href="/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a> con esso.

Da **AppView.cpp**:

```cpp
// The main function bootstraps into the IFrameworkView.
int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    winrt::init_apartment();
    CoreApplication::Run(AppViewSource());
    return 0;
}
```

Da quel momento in poi, la classe AppView gestisce l'interazione con Windows di input di base, gli eventi CoreWindow e la messaggistica e così via. Creerà anche l'holographicSpace usato dall'app.

## <a name="creating-a-win32-project"></a>Creazione di un progetto Win32

Il modo più semplice per iniziare a creare un progetto olografico Win32 è adattare l'esempio <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank"> *Win32 BasicHologram*</a>.

Questo esempio Win32 usa <a href="/windows/uwp/cpp-and-winrt-apis/" target="_blank">C++/WinRT,</a>una proiezione in linguaggio C++17 delle API di runtime di Windows che supporta qualsiasi compilatore C++17 conforme agli standard.  Il progetto illustra come creare un cubo bloccato dal mondo posizionato a 2 metri dall'utente. L'utente può premere un pulsante sul controller per posizionare il cubo in una posizione diversa specificata dallo sguardo [dell'utente.](../../design/gaze-and-commit.md) È possibile modificare questo progetto per creare qualsiasi app di realtà mista.

### <a name="win32-app-entry-point"></a>Punto di ingresso dell'app Win32

L'app Win32 olografica viene avviata nella **funzione wWinMain** in AppMain.cpp. La **funzione wWinMain** crea HWND dell'app e avvia il ciclo di messaggi.

Da **AppMain.cpp**:

```cpp
int APIENTRY wWinMain(
    _In_     HINSTANCE hInstance,
    _In_opt_ HINSTANCE hPrevInstance,
    _In_     LPWSTR    lpCmdLine,
    _In_     int       nCmdShow)
{
    UNREFERENCED_PARAMETER(hPrevInstance);
    UNREFERENCED_PARAMETER(lpCmdLine);

    winrt::init_apartment();

    App app;

    // Initialize global strings, and perform application initialization.
    app.Initialize(hInstance);

    // Create the HWND and the HolographicSpace.
    app.CreateWindowAndHolographicSpace(hInstance, nCmdShow);

    // Main message loop:
    app.Run(hInstance);

    // Perform application teardown.
    app.Uninitialize();

    return 0;
}
```

Da quel momento in poi, la classe AppMain gestisce l'interazione con i messaggi di finestra di base e così via. Creerà anche l'holographicSpace usato dall'app.

## <a name="render-holographic-content"></a>Eseguire il rendering del contenuto olografico

La cartella **Content del** progetto contiene classi per il rendering degli ologrammi nello [spazio olografico](getting-a-holographicspace.md). L'ologramma predefinito nel modello è un cubo rotante posizionato a 2 metri di distanza dall'utente. Il disegno di questo cubo viene implementato in **SpinningCubeRenderer.cpp,** che dispone di questi metodi chiave:

|  Metodo  |  Spiegazione | 
|----------|----------|
|  `CreateDeviceDependentResources` |  Carica gli shader e crea la mesh del cubo. | 
|  `PositionHologram` |  Posiziona l'ologramma nella posizione specificata <a href="/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">dall'oggetto SpatialPointerPose specificato.</a> | 
|  `Update` |  Ruota il cubo e imposta la matrice del modello. | 
|  `Render` |  Esegue il rendering di un frame usando il vertice e i pixel shader. | 

La **sottocartella Shaders** contiene quattro implementazioni di shader predefinite:

|  Shader  |  Spiegazione | 
|----------|----------|
|  `GeometryShader.hlsl` |  Pass-through che lascia invariata la geometria. | 
|  `PixelShader.hlsl` |  Passa attraverso i dati relativi al colore. I dati relativi al colore vengono interpolati e assegnati a un pixel nel passaggio di rasterizzazione. | 
|  `VertexShader.hlsl` |  Shader semplice per eseguire l'elaborazione dei vertici nella GPU. | 
|  `VPRTVertexShader.hlsl` |  Shader semplice per eseguire l'elaborazione dei vertici nella GPU, ottimizzata per Windows Mixed Reality rendering stereo. | 

`VertexShaderShared.hlsl` contiene codice comune condiviso tra `VertexShader.hlsl` e `VPRTVertexShader.hlsl` .

Nota: il modello di app Direct3D 12 include anche `ViewInstancingVertexShader.hlsl` . Questa variante usa le funzionalità facoltative D3D12 per eseguire il rendering delle immagini stereo in modo più efficiente.

Gli shader vengono compilati quando il progetto viene compilato e caricati nel metodo **SpinningCubeRenderer::CreateDeviceDependentResources.**

## <a name="interact-with-your-holograms"></a>Interagire con gli ologrammi

L'input dell'utente viene elaborato nella classe **SpatialInputHandler,** che ottiene <a href="/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">un'istanza spatialInteractionManager</a> e sottoscrive <a href="/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">l'evento SourcePressed.</a> Ciò consente di rilevare il movimento di tocco dell'aria e altri eventi di input spaziale.

## <a name="update-holographic-content"></a>Aggiornare il contenuto olografico

L'app di realtà mista viene aggiornata in un ciclo di gioco, che per impostazione predefinita viene implementato nel **metodo Update** in `AppMain.cpp` . Il **metodo Update** aggiorna gli oggetti della scena, ad esempio il cubo rotante, e restituisce un oggetto <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> usato per ottenere matrici di visualizzazione e proiezione aggiornate e per presentare la catena di scambio.

Il **metodo Render** in accetta HolographicFrame ed esegue il rendering del fotogramma corrente in ogni fotocamera `AppMain.cpp` olografica, in base all'app corrente e allo stato di posizionamento spaziale. <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank"></a>

## <a name="notes"></a>Note

Il modello Windows Mixed Reality app supporta ora la compilazione con il flag di mitigazione Spectre abilitato (/Qspectre). Assicurarsi di installare la versione con mitigazione Spectre delle librerie di runtime Microsoft Visual C++ (MSVC) prima di compilare una configurazione con mitigazione Spectre abilitata. Per installare le librerie C++ con mitigazione Spectre, avviare il Programma di installazione di Visual Studio e selezionare **Modifica.** Passare a **Singoli componenti** e cercare "spectre". Selezionare le caselle corrispondenti alle piattaforme di destinazione e alla versione MSVC cui è necessario compilare il codice con mitigazione Spectre e fare clic **su** Modifica per avviare l'installazione.

## <a name="see-also"></a>Vedi anche
* [Ottenere un HolographicSpace](getting-a-holographicspace.md)
* <a href="/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a>
* [Rendering in DirectX](rendering-in-directx.md)
* [Uso di Visual Studio per distribuzione e debug](../platform-capabilities-and-apis/using-visual-studio.md)
* [Uso dell'emulatore HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md)
* [Uso di XAML con app DirectX olografiche](../platform-capabilities-and-apis/using-xaml-with-holographic-directx-apps.md)