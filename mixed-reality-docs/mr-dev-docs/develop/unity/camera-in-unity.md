---
title: Configurazione della fotocamera in Unity
description: Informazioni su come configurare e usare la fotocamera principale di Unity per lo sviluppo di realtà mista di Windows per eseguire il rendering olografico.
author: keveleigh
ms.author: kurtie
ms.date: 03/25/2021
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, rendering olografico, olografico, immersivo, punto di messa a fuoco, buffer di profondità, solo orientamento, posizionale, opaco, trasparente, clip, auricolare realtà mista, cuffia di realtà mista di Windows, auricolare della realtà virtuale
ms.openlocfilehash: d3f69c6cf1889587b23b68259f22b34b89b925a4
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636304"
---
# <a name="camera-setup-in-unity"></a>Configurazione della fotocamera in Unity

Quando si usa una cuffia a realtà mista, diventa il centro del mondo olografico. Il componente della [fotocamera](https://docs.unity3d.com/Manual/class-Camera.html) Unity gestirà automaticamente il rendering stereoscopico e seguirà lo spostamento e la rotazione del titolo. Tuttavia, per ottimizzare completamente la qualità visiva e la [stabilità dell'ologramma](../platform-capabilities-and-apis/hologram-stability.md), è necessario impostare le impostazioni della fotocamera descritte di seguito.

## <a name="hololens-vs-vr-immersive-headsets"></a>Cuffie immersive HoloLens vs VR

Le impostazioni predefinite nel componente della fotocamera Unity sono per le applicazioni 3D tradizionali, che richiedono uno sfondo SKYBOX, perché non hanno un mondo reale.

* Quando si esegue un' **[auricolare immersiva](../../discover/immersive-headset-hardware-details.md)**, si esegue il rendering di tutti gli elementi che l'utente vede, quindi è probabile che si desideri proteggere skybox.
* Tuttavia, quando si esegue un **auricolare olografico** come [HoloLens](/hololens/hololens2-hardware), il mondo reale dovrebbe apparire dietro tutto il rendering della fotocamera. Impostare lo sfondo della fotocamera come trasparente (in HoloLens, il nero viene visualizzato come trasparente) invece di una trama skybox:
    1. Selezionare la fotocamera principale nel pannello gerarchia
    2. Nel pannello Inspector trovare il componente della fotocamera e modificare l'elenco a discesa Clear Flags da skybox a Solid Color.
    3. Selezionare la selezione dei colori di sfondo e modificare i valori di RGBA in (0, 0, 0, 0)
        1. Se si imposta questa opzione dal codice, è possibile usare Unity [`Color.clear`](https://docs.unity3d.com/ScriptReference/Color-clear.html)

[!INCLUDE[](includes/camera/opaque-camera-include.md)]

## <a name="camera-setup"></a>Impostazione della fotocamera

Indipendentemente dal tipo di esperienza che si sta sviluppando, la fotocamera principale è sempre il componente di rendering stereo primario collegato alla visualizzazione a capo del dispositivo. Il layout dell'app sarà più semplice se si immagina la posizione iniziale dell'utente come (X: 0, Y: 0, Z: 0). Poiché la fotocamera principale tiene traccia del movimento della testa dell'utente, è possibile impostare la posizione iniziale dell'utente impostando la posizione iniziale della fotocamera principale.

La scelta centrale da fare è se si sta sviluppando per auricolari HoloLens o VR immersivi. Una volta ottenuta questa procedura, passare a qualsiasi sezione di configurazione.

### <a name="hololens-camera-setup"></a>Installazione della fotocamera HoloLens

Per le app HoloLens, è necessario usare ancoraggi per tutti gli oggetti che si desidera bloccare nell'ambiente della scena. Si consiglia di usare uno spazio non vincolato per ottimizzare la stabilità e creare ancoraggi in più chat room.

[!INCLUDE[](includes/camera/hololens-setup-include.md)]

### <a name="vr-camera-setup"></a>Configurazione della fotocamera VR

La realtà mista di Windows supporta le app in un'ampia gamma di [scale di esperienza](../../design/coordinate-systems.md#mixed-reality-experience-scales), da app di solo orientamento e scalabilità verticale fino ad app a scalabilità. In HoloLens è possibile proseguire e creare app su scala mondiale che consentono agli utenti di superare i 5 metri, esplorando un'intera superficie di un edificio e oltre.

Il primo passaggio per creare un'esperienza di realtà mista in Unity consiste nel determinare quale [scalabilità dell'esperienza](../../design/coordinate-systems.md) sarà destinata all'app:

* [Orientamento o scalabilità a sedere](../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience)
* [Scalabilità in piedi o in locale](../../design/coordinate-systems.md#building-a-standing-scale-or-room-scale-experience)
* [Scalabilità globale](../../design/coordinate-systems.md#building-a-world-scale-experience)

#### <a name="room-scale-or-standing-experiences"></a>Esperienze su scala o in piedi

> [!NOTE]
> Se si sta compilando per HL2, è consigliabile creare un'esperienza a livello di occhio oppure prendere in considerazione l'uso della [comprensione della scena](../platform-capabilities-and-apis/scene-understanding-sdk.md) per ragionare sul pavimento della scena.

[!INCLUDE[](includes/camera/vr-setup-standing-include.md)]

#### <a name="seated-experiences"></a>Esperienze di seduta

[!INCLUDE[](includes/camera/vr-setup-seated-include.md)]

### <a name="setting-up-the-camera-background"></a>Impostazione dello sfondo della fotocamera

Se si usa MRTK, lo sfondo della fotocamera viene configurato e gestito automaticamente. Per i progetti di XR SDK o legacy WSA, è consigliabile impostare lo sfondo della fotocamera su nero a tinta unita in HoloLens e mantenere Skybox per VR.

## <a name="using-multiple-cameras"></a>Uso di più fotocamere

Quando nella scena sono presenti più componenti della fotocamera, Unity sa quale fotocamera usare per il rendering stereoscopico in base a quale GameObject ha il tag MainCamera. Nella versione precedente di XR, usa questo tag anche per sincronizzare il rilevamento Head. In XR SDK il rilevamento Head è gestito da uno script TrackedPoseDriver collegato alla fotocamera.

## <a name="sharing-depth-buffers"></a>Condivisione di buffer di profondità

La condivisione del buffer di profondità dell'app in Windows ogni frame offrirà all'app uno dei due aumenti di stabilità dell'ologramma, in base al tipo di auricolare per cui si esegue il rendering:

* Gli **auricolari VR immersivi** possono gestire la riproiezione posizionale quando viene fornito un buffer di profondità, regolando gli ologrammi per la stima errata nella posizione e nell'orientamento.
* Gli **auricolari HoloLens** hanno metodi diversi. HoloLens 1 seleziona automaticamente un [punto di interesse](focus-point-in-unity.md) quando viene fornito un buffer di profondità, ottimizzando la stabilità dell'ologramma lungo il piano che interseca la maggior parte del contenuto. HoloLens 2 stabilizza il contenuto usando [LSR di profondità (vedere la sezione Osservazioni)](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint).

[!INCLUDE[](includes/camera/depth-buffer-include.md)]

## <a name="using-clipping-planes"></a>Uso di piani di ritaglio

Il rendering del contenuto troppo vicino all'utente può risultare scomodo in realtà mista. È possibile regolare i [piani di ritaglio vicini e lontani](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances) sul componente della fotocamera.

1. Selezionare la **fotocamera principale** nel pannello **gerarchia**
2. Nel pannello **Inspector** trovare i **piani di ritaglio** dei componenti della **fotocamera** e modificare la casella di testo **near** da **0,3** a **0,85**. Il rendering del contenuto ancora più vicino può causare disagi da parte dell'utente e deve essere evitato in base alle [linee guida di rendering](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances).

## <a name="recentering-the-camera"></a>Ricentrare la fotocamera

Se si sta creando un' [esperienza a scalabilità verticale](../../design/coordinate-systems.md), è possibile ricentrare l'origine del mondo di Unity nella posizione Head corrente dell'utente chiamando **[XR. Metodo InputTracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** nel metodo legacy XR o **[XRInputSubsystem. TRYRECENTER](https://docs.unity3d.com/ScriptReference/XR.XRInputSubsystem.TryRecenter.html)** in XR SDK.

## <a name="teleportation"></a>Teletrasporto

Questa funzionalità è in genere riservata per le esperienze di VR:

[!INCLUDE[](includes/camera/teleport-include.md)]

## <a name="reprojection-modes"></a>Modalità di riproiezione

Sia HoloLens che le cuffie immersive riproiettano ogni frame di cui l'app esegue il rendering per adattarsi a qualsiasi stima errata della posizione effettiva dell'utente quando vengono emessi i fotoni.

Per impostazione predefinita:

* Gli **auricolari immersivi VR** si occupano della riproiezione posizionale se l'app fornisce un buffer di profondità per un determinato frame. Gli auricolari immersivi configureranno anche gli ologrammi in modo da ottenere una stima errata nella posizione e nell'orientamento. Se non viene fornito un buffer di profondità, il sistema correggerà solo le stime errate all'orientamento.
* Gli **auricolari olografici** come HoloLens 2 si occupano della riproiezione posizionale, indipendentemente dal fatto che l'app fornisca il buffer di profondità. La riproiezione posizionale è possibile senza buffer di profondità su HoloLens perché il rendering è spesso di tipo sparse con uno sfondo stabile fornito dal mondo reale.

[!INCLUDE[](includes/camera/reprojection-include.md)]

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si sta seguendo il percorso di sviluppo di Unity, si sta per esplorare i blocchi predefiniti di MRTK core. Da qui è possibile passare al blocco predefinito successivo:

> [!div class="nextstepaction"]
> [Sguardo fisso](gaze-in-unity.md)

In alternativa, passare alle API e funzionalità della piattaforma di realtà mista:

> [!div class="nextstepaction"]
> [Esperienze condivise](shared-experiences-in-unity.md)

È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#2-core-building-blocks) in qualsiasi momento.

## <a name="see-also"></a>Vedere anche

* [Stabilità degli ologrammi](../platform-capabilities-and-apis/hologram-stability.md)
* [Scale Experience](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [Fase spaziale](../../design/coordinate-systems.md#stage-frame-of-reference)
* [Perdita del rilevamento in Unity](tracking-loss-in-unity.md)
* [Ancoraggi nello spazio](../../design/spatial-anchors.md)
* [Persistenza in Unity](persistence-in-unity.md)
* [Esperienze condivise in Unity](shared-experiences-in-unity.md)
* [Ancoraggi nello spazio di Azure](/azure/spatial-anchors)
* [Azure Spatial Anchors SDK per Unity](/dotnet/api/Microsoft.Azure.SpatialAnchors)