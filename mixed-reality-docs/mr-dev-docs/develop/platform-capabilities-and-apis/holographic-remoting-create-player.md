---
title: Scrivere un lettore Holographic Remoting personalizzato
description: Creare un'app hologaphic Remoting personalizzata per visualizzare il contenuto di cui viene eseguito il rendering in un computer remoto HoloLens 2.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, Comunicazione remota, Holographic Remoting, NuGet, manifesto dell'app, contesto del lettore, app remota, visore per realtà mista, visore di realtà mista windows, visore per realtà virtuale
ms.openlocfilehash: b395f94f6c98b20f7c0c188f11a718e6da9394de5df3404e7c703558daf526f2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115190168"
---
# <a name="writing-a-custom-holographic-remoting-player-app"></a>Scrivere un'app lettore Holographic Remoting personalizzata

>[!IMPORTANT]
>Questo documento descrive la creazione di un'applicazione lettore personalizzata per HoloLens 2. I lettori personalizzati scritti per HoloLens 2 non sono compatibili con le applicazioni remote scritte per HoloLens 1. Ciò implica che entrambe le applicazioni devono NuGet pacchetto **versione 2.x.x.**

Creando un'app lettore Holographic Remoting personalizzata, è possibile [](../../design/app-views.md) creare un'applicazione personalizzata in grado di visualizzare visualizzazioni immersive da in un computer remoto nel HoloLens 2. Tutto il codice in questa pagina e i progetti di lavoro sono disponibili nel repository github degli esempi di [Holographic Remoting](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

Un lettore Holographic Remoting consente all'app di visualizzare il contenuto olografico sottoposto a rendering in un PC desktop o in un dispositivo UWP come il Xbox One con accesso a più risorse di sistema. [](rendering.md) Un'app lettore Holographic Remoting consente di trasmettere i dati di input a un'applicazione remota Holographic Remoting e di ricevere una visualizzazione immersiva come flusso video e audio. La connessione viene stabilita usando il Wi-Fi standard. Per creare un'app lettore, usare un pacchetto NuGet per aggiungere Holographic Remoting all'app UWP. Scrivere quindi il codice per gestire la connessione e visualizzare una visualizzazione immersiva. 

## <a name="prerequisites"></a>Prerequisiti

Un buon punto di partenza è un'app UWP basata su DirectX funzionante già destinata all Windows Mixed Reality APP. Per informazioni dettagliate, [vedere Panoramica dello sviluppo DirectX.](../native/directx-development-overview.md) Se non si ha un'app esistente e si vuole iniziare da zero, il modello di progetto [olografico C++](../native/creating-a-holographic-directx-project.md) è un buon punto di partenza.

>[!IMPORTANT]
>Tutte le app che usano Holographic Remoting devono essere scritte per usare un [apartment multi-thread.](/windows/win32/com/multithreaded-apartments) L'uso di [un apartment](/windows/win32/com/single-threaded-apartments) a thread singolo è supportato, ma condurrà a prestazioni non ottimali ed eventualmente a uno stub durante la riproduzione. Quando si usa C++/WinRT [winrt::init_apartment'impostazione](/windows/uwp/cpp-and-winrt-apis/get-started) predefinita è un apartment multi-thread.

## <a name="get-the-holographic-remoting-nuget-package"></a>Ottenere il pacchetto NuGet Holographic Remoting

I passaggi seguenti sono necessari per aggiungere il pacchetto NuGet a un progetto in Visual Studio.
1. Aprire il progetto in Visual Studio.
2. Fare clic con il pulsante destro del mouse sul nodo **del progetto e scegliere Gestisci NuGet pacchetti...**
3. Nel pannello visualizzato selezionare **Sfoglia** e quindi cercare "Holographic Remoting".
4. Selezionare **Microsoft.Holographic.Remoting,** assicurarsi di selezionare la versione **2.x.x** più recente e selezionare **Installa**.
5. Se viene **visualizzata la** finestra di dialogo Anteprima, selezionare **OK.**
6. Selezionare **Accetto quando** viene visualizzata la finestra di dialogo del contratto di licenza.

>[!IMPORTANT]
><a name="idl"></a>```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl```All'interno del NuGet contiene la documentazione dettagliata per l'API esposta da Holographic Remoting.

## <a name="modify-the-packageappxmanifest-of-the-application"></a>Modificare il file Package.appxmanifest dell'applicazione

Per rendere l'applicazione consapevole del Microsoft.Holographic.AppRemoting.dll aggiunto dal pacchetto NuGet, è necessario eseguire i passaggi seguenti nel progetto:

1. Nella finestra Esplora soluzioni fare clic con il pulsante destro del mouse sul file **Package.appxmanifest** e **scegliere Apri con...**
2. Selezionare **Editor XML (testo)** e selezionare **OK**
3. Aggiungere le righe seguenti al file e salvare
```xml
  </Capabilities>

  <!--Add lines below -->
  <Extensions>
    <Extension Category="windows.activatableClass.inProcessServer">
      <InProcessServer>
        <Path>Microsoft.Holographic.AppRemoting.dll</Path>
        <ActivatableClass ActivatableClassId="Microsoft.Holographic.AppRemoting.PlayerContext" ThreadingModel="both" />
      </InProcessServer>
    </Extension>
  </Extensions>
  <!--Add lines above -->

</Package>
```
## <a name="create-the-player-context"></a>Creare il contesto del lettore

Come primo passaggio, l'applicazione deve creare un contesto del lettore.

```cpp
// class declaration:

#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
// PlayerContext used to connect with a Holographic Remoting remote app and display remotely rendered frames
winrt::Microsoft::Holographic::AppRemoting::PlayerContext m_playerContext = nullptr;
```


```cpp
// class implementation:

// Create the player context
// IMPORTANT: This must be done before creating the HolographicSpace (or any other call to the Holographic API).
m_playerContext = winrt::Microsoft::Holographic::AppRemoting::PlayerContext::Create();

```

>[!WARNING]
>La comunicazione remota olografica funziona sostituendo il runtime Windows Mixed Reality che fa parte di Windows con un runtime specifico della comunicazione remota. Questa operazione viene eseguita durante la creazione del contesto del lettore. Per questo motivo, qualsiasi chiamata a qualsiasi API Windows Mixed Reality prima di creare il contesto del lettore può comportare un comportamento imprevisto. L'approccio consigliato consiste nel creare il contesto del giocatore il prima possibile prima dell'interazione con qualsiasi API di realtà mista. Non combinare mai oggetti creati o recuperati tramite un'API Windows Mixed Reality prima della chiamata a ```PlayerContext::Create``` con gli oggetti creati o recuperati successivamente.

Successivamente, è possibile creare HolographicSpace chiamando [HolographicSpace.CreateForCoreWindow](/uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow).

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-remote-app"></a>Connessione'app remota

Quando l'app lettore è pronta per il rendering del contenuto, è possibile stabilire una connessione all'app remota.

La connessione può essere stabilita in uno dei modi seguenti:
1) L'app lettore in HoloLens 2 si connette all'app remota.
2) L'app remota si connette all'app lettore in esecuzione HoloLens 2.

Per connettersi dall'app lettore all'app remota, chiamare il metodo nel ```Connect``` contesto del lettore specificando il nome host e la porta. La porta predefinita è **8265**.

```cpp
try
{
    m_playerContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    // Failed to connect. Get an error details via e.code() and e.message()
}
```

>[!IMPORTANT]
>Come per qualsiasi API C++/WinRT potrebbe generare un'eccezione ```Connect``` winrt::hresult_error che deve essere gestita.

L'ascolto delle connessioni in ingresso nell'app lettore può essere eseguito chiamando il ```Listen``` metodo . Durante questa chiamata è possibile specificare sia la porta dell'handshake che la porta di trasporto. La porta dell'handshake viene usata per l'handshake iniziale. I dati vengono quindi inviati sulla porta di trasporto. Per impostazione predefinita vengono usati i numeri di porta **8265** e **8266.**

```cpp
try
{
    m_playerContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    // Failed to listen. Get an error details via e.code() and e.message()
}
```


## <a name="handling-connection-related-events"></a>Gestione degli eventi correlati alla connessione

Espone ```PlayerContext``` tre eventi per monitorare lo stato della connessione
1) OnConnected: attivato quando è stata stabilita correttamente una connessione all'app remota.
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) OnDisconnected: attivato se una connessione stabilita viene terminata o non è stato possibile stabilire una connessione.
```cpp
m_onDisconnectedEventToken = m_playerContext.OnDisconnected([](ConnectionFailureReason failureReason)
{
    switch (failureReason)
    {
        // Handle connection failed or terminated.
        // See ConnectionFailureReason for possible reasons.
    }
}
```
>[!NOTE]
>I ```ConnectionFailureReason``` valori possibili sono documentati nel ```Microsoft.Holographic.AppRemoting.idl``` [file](#idl).

3) OnListening: quando viene avviato l'ascolto delle connessioni in ingresso.
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

È anche possibile eseguire query sullo stato della connessione usando la ```ConnectionState``` proprietà nel contesto del lettore.
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a>Visualizzare il frame sottoposto a rendering remoto

Per visualizzare il contenuto sottoposto a rendering remoto, chiamare ```PlayerContext::BlitRemoteFrame``` durante il rendering di un oggetto [HolographicFrame.](/uwp/api/windows.graphics.holographic.holographicframe) 

```BlitRemoteFrame``` richiede che il buffer nascosto per l'oggetto HolographicFrame corrente sia associato come destinazione di rendering. Il buffer nascosto può essere ricevuto da [HolographicCameraRenderingParameters](/uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) tramite la [proprietà Direct3D11BackBuffer.](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer)

Quando viene chiamato, ```BlitRemoteFrame``` copia il frame ricevuto più recente dall'applicazione remota nel BackBuffer di HolographicFrame. Viene inoltre impostato il set di punti di attivazione, se l'applicazione remota ha specificato un punto attivo durante il rendering del frame remoto.

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
>```PlayerContext::BlitRemoteFrame``` potenzialmente sovrascrive il punto attivo per il frame corrente. 
>- Per specificare un punto di attivazione di fallback, chiamare [HolographicCameraRenderingParameters::SetFocusPoint](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) prima di ```PlayerContext::BlitRemoteFrame``` . 
>- Per sovrascrivere il punto di attivazione remoto, chiamare [HolographicCameraRenderingParameters::SetFocusPoint](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)  dopo ```PlayerContext::BlitRemoteFrame``` .

In caso di esito positivo, ```BlitRemoteFrame``` restituisce ```BlitResult::Success_Color``` . In caso contrario, restituisce il motivo dell'errore:
- ```BlitResult::Failed_NoRemoteFrameAvailable```: operazione non riuscita perché non è disponibile alcun frame remoto.
- ```BlitResult::Failed_NoCamera```: operazione non riuscita perché non è presente alcuna fotocamera.
- ```BlitResult::Failed_RemoteFrameTooOld```: operazione non riuscita perché il frame remoto è troppo vecchio (vedere la proprietà PlayerContext::BlitRemoteFrameTimeout).

>[!IMPORTANT]
> A partire dalla [versione 2.1.0](holographic-remoting-version-history.md#v2.1.0) è possibile usare un lettore personalizzato per usare la riproiezione della profondità tramite Holographic Remoting.

```BlitResult``` può anche restituire ```BlitResult::Success_Color_Depth``` nelle condizioni seguenti:

- L'app remota ha eseguito il commit di un buffer di profondità [tramite HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).
- L'app lettore personalizzata ha associato un buffer di profondità valido prima di chiamare ```BlitRemoteFrame``` .

Se queste condizioni vengono soddisfatte, la profondità remota verrà ```BlitRemoteFrame``` blit nel buffer di profondità locale attualmente associato. È quindi possibile eseguire il rendering di contenuto locale aggiuntivo, che avrà un'intersezione di profondità con il contenuto sottoposto a rendering remoto. È anche possibile eseguire il commit del buffer di profondità locale tramite [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) nel lettore personalizzato in modo che la riproiezione della profondità per il contenuto di rendering remoto e locale. Per [informazioni dettagliate, vedere Riprogettazione](hologram-stability.md#reprojection) della profondità.

### <a name="projection-transform-mode"></a>Modalità di trasformazione proiezione

Un problema che si verifica quando si usa la riproiezione della profondità tramite Holographic Remoting è che è possibile eseguire il rendering del contenuto remoto con una trasformazione di proiezione diversa rispetto al contenuto locale sottoposto a rendering direttamente dall'app lettore personalizzata. Un caso d'uso comune è specificare valori diversi per il piano vicino e lontano (tramite [HolographicCamera::SetNearPlaneDistance](/uwp/api/windows.graphics.holographic.holographiccamera.setnearplanedistance) e [HolographicCamera::SetFarPlaneDistance)](/uwp/api/windows.graphics.holographic.holographiccamera.setfarplanedistance)sul lato lettore e sul lato remoto. In questo caso, non è chiaro se la trasformazione di proiezione sul lato lettore deve riflettere le distanze del piano remoto vicino/lontano o quelle locali.

A partire dalla [versione 2.1.0](holographic-remoting-version-history.md#v2.1.0) è possibile controllare la modalità di trasformazione della proiezione tramite ```PlayerContext::ProjectionTransformConfig``` . I valori supportati sono:

- ```Local``` - [HolographicCameraPose::P rojectionTransform](/uwp/api/windows.graphics.holographic.holographiccamerapose.projectiontransform) restituisce una trasformazione di proiezione che riflette le distanze del piano vicino/lontano impostate dall'app lettore personalizzata in HolographicCamera.
- ```Remote``` - La trasformazione di proiezione riflette le distanze del piano vicino/lontano specificate dall'app remota.
- ```Merged``` - Le distanze del piano near/far dall'app remota e dall'app lettore personalizzata vengono unite. Per impostazione predefinita, questa operazione viene eseguita prendendo il minimo delle distanze del piano vicino e il massimo delle distanze del piano lontano. Nel caso in cui il lato remoto o locale sia invertito, ad esempio < vicino, le distanze del piano remoto vicino/lontano vengono capovolte.

## <a name="optional-set-blitremoteframetimeout"></a>Facoltativo: impostare BlitRemoteFrameTimeout <a name="BlitRemoteFrameTimeout"></a>
>[!IMPORTANT]
> ```PlayerContext::BlitRemoteFrameTimeout```è supportato a partire dalla [versione 2.0.9.](holographic-remoting-version-history.md#v2.0.9) 

La ```PlayerContext::BlitRemoteFrameTimeout``` proprietà specifica la quantità di tempo per cui un frame remoto viene riutilizzato se non viene ricevuto alcun nuovo frame remoto. 

Un caso d'uso comune è consentire al timeout di BlitRemoteFrame di visualizzare una schermata vuota se non vengono ricevuti nuovi fotogrammi per un determinato periodo di tempo. Se abilitata, il tipo restituito del metodo può essere usato anche per passare a un contenuto di fallback di cui è stato eseguito il ```BlitRemoteFrame``` rendering locale. 

Per abilitare il timeout, impostare il valore della proprietà su una durata uguale o maggiore di 100 ms. Per disabilitare il timeout, impostare la proprietà su durata zero. Se il timeout è abilitato e non viene ricevuto alcun frame remoto per la durata impostata, BlitRemoteFrame avrà esito negativo e restituirà fino a quando non viene ricevuto un ```Failed_RemoteFrameTooOld``` nuovo frame remoto.

```cpp
using namespace std::chrono_literals;

// Set the BlitRemoteFrame timeout to 0.5s
m_playerContext.BlitRemoteFrameTimeout(500ms);
```

## <a name="optional-get-statistics-about-the-last-remote-frame"></a>Facoltativo: ottenere statistiche sull'ultimo frame remoto

Per diagnosticare problemi di prestazioni o di rete, è possibile recuperare statistiche sull'ultimo frame remoto tramite la ```PlayerContext::LastFrameStatistics``` proprietà . Le statistiche vengono aggiornate durante la chiamata a [HolographicFrame::P resentUsingCurrentPrediction](/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction).

```cpp
// Get statistics for the last presented frame.
winrt::Microsoft::Holographic::AppRemoting::PlayerFrameStatistics statistics = m_playerContext.LastFrameStatistics();
```

Per altre informazioni, vedere la ```PlayerFrameStatistics``` documentazione nel ```Microsoft.Holographic.AppRemoting.idl``` [file](#idl).

## <a name="optional-custom-data-channels"></a>Facoltativo: canali dati personalizzati

I canali dati personalizzati possono essere usati per inviare dati utente tramite la connessione remota già stabilita. Per [altre informazioni, vedere](holographic-remoting-custom-data-channels.md) canali dati personalizzati.

## <a name="see-also"></a>Vedere anche
* [Scrittura di un'app remota Holographic Remoting Windows Mixed Reality API](holographic-remoting-create-remote-wmr.md)
* [Scrittura di un'app remota Holographic Remoting con API OpenXR](holographic-remoting-create-remote-openxr.md)
* [Canali di dati di Holographic Remoting personalizzati](holographic-remoting-custom-data-channels.md)
* [Stabilire una connessione sicura con Holographic Remoting](holographic-remoting-secure-connection.md)
* [Risoluzione dei problemi e limitazioni di Holographic Remoting](holographic-remoting-troubleshooting.md)
* [Condizioni di licenza software per Holographic Remoting](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Informativa sulla privacy di Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)