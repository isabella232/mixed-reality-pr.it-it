---
ms.openlocfilehash: c7e5be36420ef14fe5aaeaafb49c0a990942339f
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636381"
---
# <a name="mrtk"></a>[<span data-ttu-id="097a1-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="097a1-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="097a1-102">Usare la classe [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) da MRTK per Unity e impostare la **scala di destinazione** su **Seated**:</span><span class="sxs-lookup"><span data-stu-id="097a1-102">Use the [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) class from MRTK for Unity and set the **Target Scale** to **Seated**:</span></span>

![Finestra Impostazioni MRTK](../../images/mrtk-target-scale.png)

<span data-ttu-id="097a1-104">MRTK deve gestire automaticamente la posizione dei playspace e della fotocamera, ma è consigliabile eseguire il doppio controllo:</span><span class="sxs-lookup"><span data-stu-id="097a1-104">MRTK should handle the position of the playspace and camera automatically, but it's good to double check:</span></span>

![Playspace MRTK](../../images/mrtk-playspace.png)

1. <span data-ttu-id="097a1-106">Nel pannello **gerarchia** espandere il GameObject **MixedRealityPlayspace** e trovare l'oggetto figlio della **fotocamera principale**</span><span class="sxs-lookup"><span data-stu-id="097a1-106">From the **Hierarchy** panel, expand the **MixedRealityPlayspace** GameObject and find the **Main Camera** child object</span></span>
2. <span data-ttu-id="097a1-107">Nel pannello **Inspector** trovare il componente **Transform** e modificare la **posizione** in **(X: 0, Y: 0, Z: 0)**</span><span class="sxs-lookup"><span data-stu-id="097a1-107">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="097a1-108">SDK XR</span><span class="sxs-lookup"><span data-stu-id="097a1-108">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="097a1-109">Impostare la modalità di origine del rilevamento su [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span><span class="sxs-lookup"><span data-stu-id="097a1-109">Set your tracking origin mode on the [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span></span> <span data-ttu-id="097a1-110">Dopo aver ottenuto il sottosistema, chiamare [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span><span class="sxs-lookup"><span data-stu-id="097a1-110">After obtaining the subsystem, call [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span></span>

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
```

<span data-ttu-id="097a1-111">E collaborano con [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)di Unity.</span><span class="sxs-lookup"><span data-stu-id="097a1-111">And work with Unity's [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html).</span></span>

![Rig XR nella gerarchia](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="097a1-113">WSA legacy</span><span class="sxs-lookup"><span data-stu-id="097a1-113">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. <span data-ttu-id="097a1-114">Passare ad **altre impostazioni** sezione delle **impostazioni di Windows Store Player**</span><span class="sxs-lookup"><span data-stu-id="097a1-114">Go to **Other Settings** section of the **Windows Store Player Settings**</span></span>
2. <span data-ttu-id="097a1-115">Scegliere la **realtà mista di Windows** come dispositivo, che può essere elencato come **Windows olografico** nelle versioni precedenti di Unity</span><span class="sxs-lookup"><span data-stu-id="097a1-115">Choose **Windows Mixed Reality** as the device, which may be listed as **Windows Holographic** in older versions of Unity</span></span>
3. <span data-ttu-id="097a1-116">Selezione della **realtà virtuale supportata**</span><span class="sxs-lookup"><span data-stu-id="097a1-116">Select **Virtual Reality Supported**</span></span>

<span data-ttu-id="097a1-117">Poiché l'oggetto fotocamera principale viene contrassegnato automaticamente come fotocamera, Unity è in tutto lo spostamento e la traduzione.</span><span class="sxs-lookup"><span data-stu-id="097a1-117">Since the Main Camera object is automatically tagged as the camera, Unity powers all movement and translation.</span></span>

>[!NOTE]
><span data-ttu-id="097a1-118">Queste impostazioni devono essere applicate alla fotocamera in ogni scena dell'app.</span><span class="sxs-lookup"><span data-stu-id="097a1-118">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="097a1-119">Per impostazione predefinita, quando si crea una nuova scena in Unity, questa conterrà una fotocamera principale GameObject nella gerarchia che include il componente della fotocamera, ma le impostazioni non sono state applicate correttamente.</span><span class="sxs-lookup"><span data-stu-id="097a1-119">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but does not have the settings below properly applied.</span></span>

<span data-ttu-id="097a1-120">**Spazio dei nomi:** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="097a1-120">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="097a1-121">**Tipo:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="097a1-121">**Type:** *XRDevice*</span></span>

<span data-ttu-id="097a1-122">Per creare un'esperienza di **solo orientamento** o **scalabilità**, è necessario impostare Unity sul tipo di spazio di rilevamento stazionario.</span><span class="sxs-lookup"><span data-stu-id="097a1-122">To build an **orientation-only** or **seated-scale experience**, you need to set Unity to the Stationary tracking space type.</span></span> <span data-ttu-id="097a1-123">Lo spazio di rilevamento fisso imposta il sistema di Coordinate internazionali di Unity per tenere traccia del [frame di riferimento fisso](../../../../design/coordinate-systems.md#spatial-coordinate-systems).</span><span class="sxs-lookup"><span data-stu-id="097a1-123">Stationary tracking space sets Unity's world coordinate system to track the [stationary frame of reference](../../../../design/coordinate-systems.md#spatial-coordinate-systems).</span></span> <span data-ttu-id="097a1-124">Nella modalità di rilevamento fisso, il contenuto inserito nell'editor appena davanti alla posizione predefinita della fotocamera (avanti è-Z) verrà visualizzato davanti all'utente all'avvio dell'app.</span><span class="sxs-lookup"><span data-stu-id="097a1-124">In the Stationary tracking mode, content placed in the editor just in front of the camera's default location (forward is -Z) will appear in front of the user when the app launches.</span></span>

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

<span data-ttu-id="097a1-125">**Spazio dei nomi:** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="097a1-125">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="097a1-126">**Tipo:** *InputTracking*</span><span class="sxs-lookup"><span data-stu-id="097a1-126">**Type:** *InputTracking*</span></span>

<span data-ttu-id="097a1-127">Per un' **esperienza solo con orientamento** puro, ad esempio un visualizzatore video di 360 gradi (dove gli aggiornamenti delle intestazioni posizionali potrebbero rovinare l'illusione), è possibile impostare [XR. InputTracking. disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) su true:</span><span class="sxs-lookup"><span data-stu-id="097a1-127">For a pure **orientation-only experience** such as a 360-degree video viewer (where positional head updates would ruin the illusion), you can then set [XR.InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) to true:</span></span>

```cs
InputTracking.disablePositionalTracking = true;
```

<span data-ttu-id="097a1-128">Per un' **esperienza a scalabilità verticale**, per consentire all'utente di ricentrare l'origine in un secondo momento, è possibile chiamare [XR. Metodo InputTracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) :</span><span class="sxs-lookup"><span data-stu-id="097a1-128">For a **seated-scale experience**, to let the user later recenter the seated origin, you can call the [XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) method:</span></span>

```cs
InputTracking.Recenter();
```

<span data-ttu-id="097a1-129">Se si sta creando un' [esperienza a scalabilità verticale](../../../../design/coordinate-systems.md), è possibile ricentrare l'origine del mondo di Unity nella posizione Head corrente dell'utente chiamando **[XR. Metodo InputTracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** .</span><span class="sxs-lookup"><span data-stu-id="097a1-129">If you're building a [seated-scale experience](../../../../design/coordinate-systems.md), you can recenter Unity's world origin at the user's current head position by calling the **[XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** method.</span></span>