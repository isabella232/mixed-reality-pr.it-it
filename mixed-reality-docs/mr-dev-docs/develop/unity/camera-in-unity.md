---
title: Configurazione della fotocamera in Unity
description: Informazioni su come configurare e usare la fotocamera principale di Unity per lo Windows Mixed Reality per eseguire il rendering olografico.
author: keveleigh
ms.author: kurtie
ms.date: 03/25/2021
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, rendering olografico, olografico, immersive, punto di messa a fuoco, buffer di profondità, solo orientamento, posizionale, opaco, trasparente, clip, visore VR di realtà mista, visore VR windows mixed reality, visore VR di realtà virtuale
ms.openlocfilehash: 1ac8c16e7bdd6b85b05c837e1a27fbd1e4cf4489ccb03d10ea5e952b2656cbe8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212292"
---
# <a name="camera-setup-in-unity"></a>Configurazione della fotocamera in Unity

Quando indossi un visore VR di realtà mista, diventa il centro del tuo mondo olografico. Il componente [Fotocamera unity](https://docs.unity3d.com/Manual/class-Camera.html) gestirà automaticamente il rendering stereoscopico e seguirà il movimento e la rotazione della testa. Tuttavia, per ottimizzare completamente la qualità visiva e [la stabilità degli ologrammi,](../platform-capabilities-and-apis/hologram-stability.md)è necessario impostare le impostazioni della fotocamera descritte di seguito.

## <a name="hololens-vs-vr-immersive-headsets"></a>HoloLens visori VR immersive

Le impostazioni predefinite nel componente Fotocamera unity sono per le applicazioni 3D tradizionali, che necessitano di uno sfondo simile a skybox perché non hanno un mondo reale.

* Quando si esegue su un **[visore VR immersive,](../../discover/immersive-headset-hardware-details.md)** si esegue il rendering di tutto ciò che l'utente vede ed è quindi probabile che si voglia mantenere skybox.
* Tuttavia, quando si esegue su un visore VR **olografico** come [HoloLens](/hololens/hololens2-hardware), il mondo reale dovrebbe apparire dietro tutto ciò che la fotocamera esegue il rendering. Imposta lo sfondo della fotocamera in modo che sia trasparente (in HoloLens il rendering nero come trasparente) invece di una trama Skybox:
    1. Selezionare la fotocamera principale nel pannello Gerarchia
    2. Nel pannello Inspector (Controllo) trova il componente Camera (Fotocamera) e modifica l'elenco a discesa Clear Flags (Cancella flag) da Skybox a Solid Color (Colore a tinta unita)
    3. Selezionare la selezione colori di sfondo e modificare i valori di RGBA in (0, 0, 0, 0)
        1. Se si imposta questa opzione dal codice, è possibile usare il file di Unity [`Color.clear`](https://docs.unity3d.com/ScriptReference/Color-clear.html)

[!INCLUDE[](includes/camera/opaque-camera-include.md)]

## <a name="camera-setup"></a>Impostazione della fotocamera

Indipendentemente dal tipo di esperienza che stai sviluppando, la fotocamera principale è sempre il componente principale per il rendering stereo collegato al display montato con la testa del dispositivo. Il posizionamento dell'app sarà più semplice se si immaginare la posizione iniziale dell'utente come (X: 0, Y: 0, Z: 0). Poiché la fotocamera principale traccia il movimento della testa dell'utente, la posizione iniziale dell'utente può essere impostata impostando la posizione iniziale della fotocamera principale.

La scelta fondamentale da effettuare è lo sviluppo per visori VR immersive o HoloLens visori VR. Una volta ottenuto questo, passare alla sezione di configurazione applicabile.

### <a name="hololens-camera-setup"></a>HoloLens della fotocamera

Per HoloLens app, è necessario usare ancoraggi per tutti gli oggetti che si vuole bloccare nell'ambiente della scena. È consigliabile usare lo spazio illimitato per ottimizzare la stabilità e creare ancoraggi in più stanze.

[!INCLUDE[](includes/camera/hololens-setup-include.md)]

### <a name="vr-camera-setup"></a>Configurazione della fotocamera VR

Windows Mixed Reality supporta le app in un'ampia gamma di scalabilità di [esperienze,](../../design/coordinate-systems.md#mixed-reality-experience-scales)dalle app con solo orientamento e da posti a posto fino alle app a scalabilità di stanza. In HoloLens è possibile andare oltre e creare app su scala globale che consentono agli utenti di superare i 5 metri, esplorando un intero piano di un edificio e oltre.

Il primo passaggio per creare un'esperienza di realtà mista in Unity consiste nel determinare la [scalabilità dell'esperienza](../../design/coordinate-systems.md) di destinazione dell'app:

* [Orientamento o scala da disegno](../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience)
* [In piedi o su scala locale](../../design/coordinate-systems.md#building-a-standing-scale-or-room-scale-experience)
* [Scalabilità globale](../../design/coordinate-systems.md#building-a-world-scale-experience)

#### <a name="room-scale-or-standing-experiences"></a>Esperienze in scala o in piedi

> [!NOTE]
> Se si sta creando per HL2, è consigliabile creare un'esperienza a livello oculare o prendere in considerazione l'uso di [Scene Understanding](../platform-capabilities-and-apis/scene-understanding-sdk.md) per valutare il piano della scena.

[!INCLUDE[](includes/camera/vr-setup-standing-include.md)]

#### <a name="seated-experiences"></a>Esperienze da posti a parte

[!INCLUDE[](includes/camera/vr-setup-seated-include.md)]

### <a name="setting-up-the-camera-background"></a>Configurazione dello sfondo della fotocamera

Se si usa MRTK, lo sfondo della fotocamera viene configurato e gestito automaticamente. Per i progetti XR SDK o WSA legacy, è consigliabile impostare lo sfondo della fotocamera su nero a tinta unita HoloLens mantenendo lo skybox per la realtà virtuale.

## <a name="using-multiple-cameras"></a>Uso di più fotocamere

Quando sono presenti più componenti camera nella scena, Unity sa quale fotocamera usare per il rendering stereoscopico in base a quale GameObject ha il tag MainCamera. In XR legacy, usa anche questo tag per sincronizzare il rilevamento head. In XR SDK il rilevamento della testa è basato su uno script TrackedPoseDriver collegato alla fotocamera.

## <a name="sharing-depth-buffers"></a>Condivisione dei buffer di profondità

La condivisione del buffer di profondità dell'app Windows ogni fotogramma offrirà all'app uno dei due boost in stabilità dell'ologramma, in base al tipo di visore VR per cui si esegue il rendering:

* **I visori VR** immersive possono occuparsi della riproiezione posizionale quando viene fornito un buffer di profondità, regolando gli ologrammi per una errata interpretazione sia nella posizione che nell'orientamento.
* **HoloLens visori** VR hanno diversi metodi. HoloLens 1 selezionerà automaticamente [](focus-point-in-unity.md) un punto attivo quando viene fornito un buffer di profondità, ottimizzando la stabilità dell'ologramma lungo il piano che interseca la maggior parte del contenuto. HoloLens 2 stabilizza il contenuto usando [depth LSR (vedere la sezione Osservazioni).](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)

[!INCLUDE[](includes/camera/depth-buffer-include.md)]

## <a name="using-clipping-planes"></a>Uso dei piani di ritaglio

Il rendering del contenuto troppo vicino all'utente può essere di grande disagi nella realtà mista. È possibile regolare i [piani di ritaglio vicino e lontano](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances) sul componente Fotocamera.

1. Selezionare la **fotocamera principale** nel pannello **Gerarchia**
2. Nel pannello **Inspector (Controllo)** trova il componente **Camera** **Clipping Planes (Piani** di ritaglio) e modifica la casella di testo **Near** (Vicino) da **0,3** a **0,85.** Il rendering del contenuto ancora più vicino può causare disagi per l'utente e deve essere evitato in base alle linee [guida sulla distanza di rendering.](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances)

## <a name="recentering-the-camera"></a>Recentering della fotocamera

Se stai creando un'esperienza su larga [scala,](../../design/coordinate-systems.md)puoi usare l'origine globale di Unity più recente nella posizione attuale della testa dell'utente chiamando **[XR. Metodo InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** in XR legacy o **[metodo XRInputSubsystem.TryRecenter](https://docs.unity3d.com/ScriptReference/XR.XRInputSubsystem.TryRecenter.html)** in XR SDK.

## <a name="teleportation"></a>Teletrasporto

Questa funzionalità è in genere riservata per le esperienze di realtà virtuale:

[!INCLUDE[](includes/camera/teleport-include.md)]

## <a name="reprojection-modes"></a>Modalità di riproiezione

Sia HoloLens visori VR immersive riprogetteranno ogni fotogramma di cui l'app esegue il rendering per adattarsi a qualsiasi errata interpretazione della posizione effettiva della testa dell'utente quando vengono emessi fotoni.

Per impostazione predefinita:

* **I visori VR immersive si** occuperanno della nuovaproiezione posizionale se l'app fornisce un buffer di profondità per un determinato fotogramma. I visori VR immersive regolano anche gli ologrammi in modo da essere interpretati in modo non corretto sia nella posizione che nell'orientamento. Se non viene specificato un buffer di profondità, il sistema correggerà solo le precondizioni erre nell'orientamento.
* **I visori VR olografici** come HoloLens 2 si occuperanno della riproiezione posizionale indipendentemente dal fatto che l'app ofrimi o meno il buffer di profondità. La riproiezione posizionale è possibile senza buffer di profondità HoloLens poiché il rendering è spesso sparse con uno sfondo stabile fornito dal mondo reale.

[!INCLUDE[](includes/camera/reprojection-include.md)]

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si sta seguendo il percorso di sviluppo di Unity che è stato strutturato, si stanno esplorando i blocchi predefiniti principali di MRTK. Da qui è possibile passare al blocco predefinito successivo:

> [!div class="nextstepaction"]
> [Sguardo fisso](gaze-in-unity.md)

In alternativa, passare alle API e funzionalità della piattaforma di realtà mista:

> [!div class="nextstepaction"]
> [Esperienze condivise](shared-experiences-in-unity.md)

È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#2-core-building-blocks) in qualsiasi momento.

## <a name="see-also"></a>Vedere anche

* [Stabilità degli ologrammi](../platform-capabilities-and-apis/hologram-stability.md)
* [Scale dell'esperienza](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [Fase spaziale](../../design/coordinate-systems.md#stage-frame-of-reference)
* [Perdita del rilevamento in Unity](tracking-loss-in-unity.md)
* [Ancoraggi nello spazio](../../design/spatial-anchors.md)
* [Persistenza in Unity](persistence-in-unity.md)
* [Esperienze condivise in Unity](shared-experiences-in-unity.md)
* [Ancoraggi nello spazio di Azure](/azure/spatial-anchors)
* [Azure Spatial Anchors SDK per Unity](/dotnet/api/Microsoft.Azure.SpatialAnchors)