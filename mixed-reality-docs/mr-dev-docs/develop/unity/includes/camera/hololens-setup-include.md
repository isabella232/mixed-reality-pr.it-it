---
ms.openlocfilehash: 7470690a96380184ead7319d4461005042c6db82
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636323"
---
# <a name="mrtk"></a>[<span data-ttu-id="99f74-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="99f74-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="99f74-102">Seguire questa [esercitazione dettagliata](../../tutorials/mr-learning-base-01.md) per aggiungere e configurare automaticamente il Toolkit di realtà mista nel progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="99f74-102">Follow this [step-by-step tutorial](../../tutorials/mr-learning-base-01.md) to add and automatically configure Mixed Reality Toolkit in your Unity project.</span></span> <span data-ttu-id="99f74-103">È anche possibile usare direttamente la classe [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) da MRTK per Unity e impostare la scala di **destinazione** su **World**:</span><span class="sxs-lookup"><span data-stu-id="99f74-103">It's also possible to work directly with the [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) class from MRTK for Unity and set the **Target Scale** to **World**:</span></span>

![Finestra Impostazioni MRTK](../../images/mrtk-target-scale.png)

<span data-ttu-id="99f74-105">MRTK deve gestire automaticamente la posizione dei playspace e della fotocamera, ma è consigliabile eseguire il doppio controllo:</span><span class="sxs-lookup"><span data-stu-id="99f74-105">MRTK should handle the position of the playspace and camera automatically, but it's good to double check:</span></span>

![Playspace MRTK](../../images/mrtk-playspace.png)

1. <span data-ttu-id="99f74-107">Nel pannello **gerarchia** espandere il GameObject **MixedRealityPlayspace** e trovare l'oggetto figlio della **fotocamera principale**</span><span class="sxs-lookup"><span data-stu-id="99f74-107">From the **Hierarchy** panel, expand the **MixedRealityPlayspace** GameObject and find the **Main Camera** child object</span></span>
2. <span data-ttu-id="99f74-108">Nel pannello **Inspector** trovare il componente **Transform** e modificare la **posizione** in **(X: 0, Y: 0, Z: 0)**</span><span class="sxs-lookup"><span data-stu-id="99f74-108">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="99f74-109">SDK XR</span><span class="sxs-lookup"><span data-stu-id="99f74-109">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="99f74-110">Impostare la modalità di origine del rilevamento su [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span><span class="sxs-lookup"><span data-stu-id="99f74-110">Set your tracking origin mode on the [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span></span> <span data-ttu-id="99f74-111">Dopo aver ottenuto il sottosistema, chiamare [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span><span class="sxs-lookup"><span data-stu-id="99f74-111">After obtaining the subsystem, call [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span></span>

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Unbounded); // Recommendation for OpenXR
```

<span data-ttu-id="99f74-112">È possibile usare [ARSession](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.1/manual/index.html#installing-ar-foundation) per le applicazioni HoloLens, che funziona meglio con gli ancoraggi e con ARKit/ARCore.</span><span class="sxs-lookup"><span data-stu-id="99f74-112">You can use [ARSession](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.1/manual/index.html#installing-ar-foundation) for HoloLens applications, which works better with anchors and ARKit/ARCore.</span></span>

![Sessione AR nella gerarchia](../../images/xrsdk-arsession.png)

> [!IMPORTANT]
> <span data-ttu-id="99f74-114">Per la sessione AR e le funzionalità correlate è necessario che sia installato AR Foundation.</span><span class="sxs-lookup"><span data-stu-id="99f74-114">AR Session and related features need AR Foundation installed.</span></span>

<span data-ttu-id="99f74-115">È anche possibile applicare manualmente le modifiche della fotocamera senza usare ARSession:</span><span class="sxs-lookup"><span data-stu-id="99f74-115">It's also possible to apply the camera changes manually without using ARSession:</span></span>

1. <span data-ttu-id="99f74-116">Selezionare la **fotocamera principale** nel pannello **gerarchia**</span><span class="sxs-lookup"><span data-stu-id="99f74-116">Select **Main Camera** in the **Hierarchy** panel</span></span>
1. <span data-ttu-id="99f74-117">Nel pannello **Inspector** trovare il componente **Transform** e modificare la **posizione** in **(X: 0, Y: 0, Z: 0)**</span><span class="sxs-lookup"><span data-stu-id="99f74-117">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

   <span data-ttu-id="99f74-118">![Fotocamera nel riquadro controllo in Unity](../../images/maincamera-350px.png)</span><span class="sxs-lookup"><span data-stu-id="99f74-118">![Camera in the Inspector pane in Unity](../../images/maincamera-350px.png)</span></span>  
   <span data-ttu-id="99f74-119">*Fotocamera nel riquadro controllo in Unity*</span><span class="sxs-lookup"><span data-stu-id="99f74-119">*Camera in the Inspector pane in Unity*</span></span>

1. <span data-ttu-id="99f74-120">Aggiungere un **TrackedPoseDriver** alla **fotocamera principale**</span><span class="sxs-lookup"><span data-stu-id="99f74-120">Add a **TrackedPoseDriver** to the **Main Camera**</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="99f74-121">WSA legacy</span><span class="sxs-lookup"><span data-stu-id="99f74-121">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. <span data-ttu-id="99f74-122">Selezionare la **fotocamera principale** nel pannello **gerarchia**</span><span class="sxs-lookup"><span data-stu-id="99f74-122">Select **Main Camera** in the **Hierarchy** panel</span></span>
1. <span data-ttu-id="99f74-123">Nel pannello **Inspector** trovare il componente **Transform** e modificare la **posizione** in **(X: 0, Y: 0, Z: 0)**</span><span class="sxs-lookup"><span data-stu-id="99f74-123">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

   <span data-ttu-id="99f74-124">![Fotocamera nel riquadro controllo in Unity](../../images/maincamera-350px.png)</span><span class="sxs-lookup"><span data-stu-id="99f74-124">![Camera in the Inspector pane in Unity](../../images/maincamera-350px.png)</span></span>  
   <span data-ttu-id="99f74-125">*Fotocamera nel riquadro controllo in Unity*</span><span class="sxs-lookup"><span data-stu-id="99f74-125">*Camera in the Inspector pane in Unity*</span></span>

1. <span data-ttu-id="99f74-126">Passare ad **altre impostazioni** sezione delle **impostazioni di Windows Store Player**</span><span class="sxs-lookup"><span data-stu-id="99f74-126">Go to **Other Settings** section of the **Windows Store Player Settings**</span></span>
1. <span data-ttu-id="99f74-127">Scegliere la **realtà mista di Windows** come dispositivo, che può essere elencato come **Windows olografico** nelle versioni precedenti di Unity</span><span class="sxs-lookup"><span data-stu-id="99f74-127">Choose **Windows Mixed Reality** as the device, which may be listed as **Windows Holographic** in older versions of Unity</span></span>
1. <span data-ttu-id="99f74-128">Selezione della **realtà virtuale supportata**</span><span class="sxs-lookup"><span data-stu-id="99f74-128">Select **Virtual Reality Supported**</span></span>

<span data-ttu-id="99f74-129">Poiché l'oggetto fotocamera principale viene contrassegnato automaticamente come fotocamera, Unity è in tutto lo spostamento e la traduzione.</span><span class="sxs-lookup"><span data-stu-id="99f74-129">Since the Main Camera object is automatically tagged as the camera, Unity powers all movement and translation.</span></span>

>[!NOTE]
><span data-ttu-id="99f74-130">Queste impostazioni devono essere applicate alla fotocamera in ogni scena dell'app.</span><span class="sxs-lookup"><span data-stu-id="99f74-130">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="99f74-131">Per impostazione predefinita, quando si crea una nuova scena in Unity, questa conterrà una fotocamera principale GameObject nella gerarchia che include il componente della fotocamera, ma potrebbe non avere le impostazioni applicate correttamente.</span><span class="sxs-lookup"><span data-stu-id="99f74-131">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but may not have the settings properly applied.</span></span>