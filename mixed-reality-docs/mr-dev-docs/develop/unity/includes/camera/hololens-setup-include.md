---
ms.openlocfilehash: 6e751f5376110ddc6ae92c75b4182fba8240a356
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748470"
---
# <a name="mrtk"></a>[<span data-ttu-id="7804f-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="7804f-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="7804f-102">Seguire questa [esercitazione dettagliata per aggiungere](../../tutorials/mr-learning-base-01.md) e configurare automaticamente Mixed Reality Toolkit nel progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="7804f-102">Follow this [step-by-step tutorial](../../tutorials/mr-learning-base-01.md) to add and automatically configure Mixed Reality Toolkit in your Unity project.</span></span> <span data-ttu-id="7804f-103">È anche possibile usare direttamente la classe [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) di MRTK per Unity e impostare La scala **di** destinazione su **World:**</span><span class="sxs-lookup"><span data-stu-id="7804f-103">It's also possible to work directly with the [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) class from MRTK for Unity and set the **Target Scale** to **World**:</span></span>

![Finestra delle impostazioni di MRTK](../../images/mrtk-target-scale.png)

<span data-ttu-id="7804f-105">MRTK deve gestire automaticamente la posizione dello spazio di riproduzione e della fotocamera, ma è consigliabile eseguire un controllo doppio:</span><span class="sxs-lookup"><span data-stu-id="7804f-105">MRTK should handle the position of the playspace and camera automatically, but it's good to double check:</span></span>

![Spazio di riproduzione MRTK](../../images/mrtk-playspace.png)

1. <span data-ttu-id="7804f-107">Nel pannello **Hierarchy (Gerarchia)** espandi **MixedRealityPlayspace** GameObject e trova l'oggetto figlio Main Camera **(Fotocamera** principale)</span><span class="sxs-lookup"><span data-stu-id="7804f-107">From the **Hierarchy** panel, expand the **MixedRealityPlayspace** GameObject and find the **Main Camera** child object</span></span>
2. <span data-ttu-id="7804f-108">Nel pannello **Inspector (Controllo)** trova il **componente Transform** (Trasforma) e modifica **Position (Posizione)** in **(X: 0, Y: 0, Z: 0)**</span><span class="sxs-lookup"><span data-stu-id="7804f-108">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="7804f-109">XR SDK</span><span class="sxs-lookup"><span data-stu-id="7804f-109">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="7804f-110">Impostare la modalità di origine di rilevamento in [XRInputSubsystem.](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html)</span><span class="sxs-lookup"><span data-stu-id="7804f-110">Set your tracking origin mode on the [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span></span> <span data-ttu-id="7804f-111">Dopo aver ottenuto il sottosistema, chiamare [TrySetTrackingOriginMode:](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html)</span><span class="sxs-lookup"><span data-stu-id="7804f-111">After obtaining the subsystem, call [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span></span>

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Unbounded); // Recommendation for OpenXR
```

<span data-ttu-id="7804f-112">Puoi usare [ARSession per](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.1/manual/index.html#installing-ar-foundation) le applicazioni HoloLens, che funziona meglio con gli ancoraggi e ARKit/ARCore.</span><span class="sxs-lookup"><span data-stu-id="7804f-112">You can use [ARSession](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.1/manual/index.html#installing-ar-foundation) for HoloLens applications, which works better with anchors and ARKit/ARCore.</span></span>

![Sessione AR nella gerarchia](../../images/xrsdk-arsession.png)

> [!IMPORTANT]
> <span data-ttu-id="7804f-114">Ar Session e le funzionalità correlate necessitano dell'installazione di AR Foundation.</span><span class="sxs-lookup"><span data-stu-id="7804f-114">AR Session and related features need AR Foundation installed.</span></span>

<span data-ttu-id="7804f-115">È anche possibile applicare manualmente le modifiche della fotocamera senza usare ARSession:</span><span class="sxs-lookup"><span data-stu-id="7804f-115">It's also possible to apply the camera changes manually without using ARSession:</span></span>

1. <span data-ttu-id="7804f-116">Selezionare **Main Camera (Fotocamera** principale) nel **pannello Hierarchy (Gerarchia)**</span><span class="sxs-lookup"><span data-stu-id="7804f-116">Select **Main Camera** in the **Hierarchy** panel</span></span>
1. <span data-ttu-id="7804f-117">Nel pannello **Inspector (Controllo)** trova il **componente Transform** (Trasforma) e modifica **Position (Posizione)** in **(X: 0, Y: 0, Z: 0)**</span><span class="sxs-lookup"><span data-stu-id="7804f-117">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

   <span data-ttu-id="7804f-118">![Fotocamera nel riquadro Inspector (Controllo) in Unity](../../images/maincamera-350px.png)</span><span class="sxs-lookup"><span data-stu-id="7804f-118">![Camera in the Inspector pane in Unity](../../images/maincamera-350px.png)</span></span>  
   <span data-ttu-id="7804f-119">*Fotocamera nel riquadro Inspector (Controllo) in Unity*</span><span class="sxs-lookup"><span data-stu-id="7804f-119">*Camera in the Inspector pane in Unity*</span></span>

1. <span data-ttu-id="7804f-120">Aggiungere **trackedPoseDriver** alla fotocamera **principale**</span><span class="sxs-lookup"><span data-stu-id="7804f-120">Add a **TrackedPoseDriver** to the **Main Camera**</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="7804f-121">Legacy WSA</span><span class="sxs-lookup"><span data-stu-id="7804f-121">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. <span data-ttu-id="7804f-122">Selezionare **Main Camera (Fotocamera** principale) nel **pannello Hierarchy (Gerarchia)**</span><span class="sxs-lookup"><span data-stu-id="7804f-122">Select **Main Camera** in the **Hierarchy** panel</span></span>
1. <span data-ttu-id="7804f-123">Nel pannello **Inspector (Controllo)** trova il **componente Transform** (Trasforma) e modifica **Position (Posizione)** in **(X: 0, Y: 0, Z: 0)**</span><span class="sxs-lookup"><span data-stu-id="7804f-123">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

   <span data-ttu-id="7804f-124">![Fotocamera nel riquadro Inspector (Controllo) in Unity](../../images/maincamera-350px.png)</span><span class="sxs-lookup"><span data-stu-id="7804f-124">![Camera in the Inspector pane in Unity](../../images/maincamera-350px.png)</span></span>  
   <span data-ttu-id="7804f-125">*Fotocamera nel riquadro Inspector (Controllo) in Unity*</span><span class="sxs-lookup"><span data-stu-id="7804f-125">*Camera in the Inspector pane in Unity*</span></span>

1. <span data-ttu-id="7804f-126">Passare alla **sezione Altre impostazioni** delle impostazioni di Windows Store **Player**</span><span class="sxs-lookup"><span data-stu-id="7804f-126">Go to **Other Settings** section of the **Windows Store Player Settings**</span></span>
1. <span data-ttu-id="7804f-127">Scegliere **Windows Mixed Reality** come dispositivo, che potrebbe essere elencato come **Windows Holographic** nelle versioni precedenti di Unity</span><span class="sxs-lookup"><span data-stu-id="7804f-127">Choose **Windows Mixed Reality** as the device, which may be listed as **Windows Holographic** in older versions of Unity</span></span>
1. <span data-ttu-id="7804f-128">Selezionare **Virtual Reality Supported (Realtà virtuale supportata)**</span><span class="sxs-lookup"><span data-stu-id="7804f-128">Select **Virtual Reality Supported**</span></span>

<span data-ttu-id="7804f-129">Poiché l'oggetto Main Camera viene automaticamente contrassegnato come fotocamera, Unity alimenta tutti i movimenti e le traduzioni.</span><span class="sxs-lookup"><span data-stu-id="7804f-129">Since the Main Camera object is automatically tagged as the camera, Unity powers all movement and translation.</span></span>

>[!NOTE]
><span data-ttu-id="7804f-130">Queste impostazioni devono essere applicate alla fotocamera in ogni scena dell'app.</span><span class="sxs-lookup"><span data-stu-id="7804f-130">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="7804f-131">Per impostazione predefinita, quando crei una nuova scena in Unity, conterrà un GameObject della fotocamera principale nella gerarchia che include il componente Fotocamera, ma potrebbe non avere le impostazioni applicate correttamente.</span><span class="sxs-lookup"><span data-stu-id="7804f-131">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but may not have the settings properly applied.</span></span>