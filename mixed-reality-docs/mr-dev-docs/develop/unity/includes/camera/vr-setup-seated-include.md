---
ms.openlocfilehash: 3bffb5db8f4a36d04c2b408c939cbd2010a7def7
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748475"
---
# <a name="mrtk"></a>[<span data-ttu-id="f8cee-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="f8cee-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="f8cee-102">Usare la [classe MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) di MRTK per Unity e impostare **Scala di** destinazione **su Seated:**</span><span class="sxs-lookup"><span data-stu-id="f8cee-102">Use the [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) class from MRTK for Unity and set the **Target Scale** to **Seated**:</span></span>

![Finestra delle impostazioni MRTK](../../images/mrtk-target-scale.png)

<span data-ttu-id="f8cee-104">MRTK deve gestire automaticamente la posizione dello spazio di riproduzione e della fotocamera, ma è consigliabile eseguire un doppio controllo:</span><span class="sxs-lookup"><span data-stu-id="f8cee-104">MRTK should handle the position of the playspace and camera automatically, but it's good to double check:</span></span>

![Spazio di riproduzione MRTK](../../images/mrtk-playspace.png)

1. <span data-ttu-id="f8cee-106">Nel pannello **Gerarchia** espandere **MixedRealityPlayspace** GameObject e trovare l'oggetto **figlio Main Camera**</span><span class="sxs-lookup"><span data-stu-id="f8cee-106">From the **Hierarchy** panel, expand the **MixedRealityPlayspace** GameObject and find the **Main Camera** child object</span></span>
2. <span data-ttu-id="f8cee-107">Nel pannello **Inspector** (Controllo) trovare **il componente Transform** (Trasforma) e impostare Position **(Posizione)** su **(X: 0, Y: 0, Z: 0)**</span><span class="sxs-lookup"><span data-stu-id="f8cee-107">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="f8cee-108">XR SDK</span><span class="sxs-lookup"><span data-stu-id="f8cee-108">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="f8cee-109">Impostare la modalità di origine di rilevamento in [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span><span class="sxs-lookup"><span data-stu-id="f8cee-109">Set your tracking origin mode on the [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span></span> <span data-ttu-id="f8cee-110">Dopo aver ottenuto il sottosistema, chiamare [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span><span class="sxs-lookup"><span data-stu-id="f8cee-110">After obtaining the subsystem, call [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span></span>

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
```

<span data-ttu-id="f8cee-111">E usare [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)di Unity.</span><span class="sxs-lookup"><span data-stu-id="f8cee-111">And work with Unity's [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html).</span></span>

![Rig XR nella gerarchia](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="f8cee-113">Legacy WSA</span><span class="sxs-lookup"><span data-stu-id="f8cee-113">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. <span data-ttu-id="f8cee-114">Passare alla **sezione Altre impostazioni** delle impostazioni di Windows Store **Player**</span><span class="sxs-lookup"><span data-stu-id="f8cee-114">Go to **Other Settings** section of the **Windows Store Player Settings**</span></span>
2. <span data-ttu-id="f8cee-115">Scegliere **Windows Mixed Reality** come dispositivo, che potrebbe essere elencato come **Windows Holographic** nelle versioni precedenti di Unity</span><span class="sxs-lookup"><span data-stu-id="f8cee-115">Choose **Windows Mixed Reality** as the device, which may be listed as **Windows Holographic** in older versions of Unity</span></span>
3. <span data-ttu-id="f8cee-116">Selezionare **Realtà virtuale supportata**</span><span class="sxs-lookup"><span data-stu-id="f8cee-116">Select **Virtual Reality Supported**</span></span>

<span data-ttu-id="f8cee-117">Poiché l'oggetto Fotocamera principale viene contrassegnato automaticamente come fotocamera, Unity alimenta tutti i movimenti e la traduzione.</span><span class="sxs-lookup"><span data-stu-id="f8cee-117">Since the Main Camera object is automatically tagged as the camera, Unity powers all movement and translation.</span></span>

>[!NOTE]
><span data-ttu-id="f8cee-118">Queste impostazioni devono essere applicate alla fotocamera in ogni scena dell'app.</span><span class="sxs-lookup"><span data-stu-id="f8cee-118">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="f8cee-119">Per impostazione predefinita, quando si crea una nuova scena in Unity, questa conterrà un oggetto GameObject della fotocamera principale nella gerarchia che include il componente Fotocamera, ma non avrà le impostazioni seguenti applicate correttamente.</span><span class="sxs-lookup"><span data-stu-id="f8cee-119">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but does not have the settings below properly applied.</span></span>

<span data-ttu-id="f8cee-120">**Spazio dei nomi:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="f8cee-120">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="f8cee-121">**Tipo:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="f8cee-121">**Type:** *XRDevice*</span></span>

<span data-ttu-id="f8cee-122">Per creare **un'esperienza solo orientamento** o su scala da seduti, è necessario impostare Unity sul tipo di spazio di rilevamento stazionario. </span><span class="sxs-lookup"><span data-stu-id="f8cee-122">To build an **orientation-only** or **seated-scale experience**, you need to set Unity to the Stationary tracking space type.</span></span> <span data-ttu-id="f8cee-123">Lo spazio di rilevamento stazionario imposta il sistema di coordinate del mondo di Unity per tenere traccia [del fotogramma stazionario di riferimento.](../../../../design/coordinate-systems.md#spatial-coordinate-systems)</span><span class="sxs-lookup"><span data-stu-id="f8cee-123">Stationary tracking space sets Unity's world coordinate system to track the [stationary frame of reference](../../../../design/coordinate-systems.md#spatial-coordinate-systems).</span></span> <span data-ttu-id="f8cee-124">Nella modalità di rilevamento stazionario, il contenuto posizionato nell'editor proprio davanti alla posizione predefinita della fotocamera (forward è -Z) verrà visualizzato davanti all'utente all'avvio dell'app.</span><span class="sxs-lookup"><span data-stu-id="f8cee-124">In the Stationary tracking mode, content placed in the editor just in front of the camera's default location (forward is -Z) will appear in front of the user when the app launches.</span></span>

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

<span data-ttu-id="f8cee-125">**Spazio dei nomi:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="f8cee-125">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="f8cee-126">**Tipo:** *InputTracking*</span><span class="sxs-lookup"><span data-stu-id="f8cee-126">**Type:** *InputTracking*</span></span>

<span data-ttu-id="f8cee-127">Per **un'esperienza** pura solo con orientamento, ad esempio un visualizzatore video a 360 gradi (in cui gli aggiornamenti della testa posizionale avrebbero distrutto l'illusione), è quindi possibile impostare [XR. InputTracking.disablePositionalTracking su](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) true:</span><span class="sxs-lookup"><span data-stu-id="f8cee-127">For a pure **orientation-only experience** such as a 360-degree video viewer (where positional head updates would ruin the illusion), you can then set [XR.InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) to true:</span></span>

```cs
InputTracking.disablePositionalTracking = true;
```

<span data-ttu-id="f8cee-128">Per **un'esperienza su larga scala,** per consentire all'utente di eseguire in seguito una versione più recente dell'origine da seduti, è possibile chiamare [il metodo XR. Metodo InputTracking.Recenter:](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)</span><span class="sxs-lookup"><span data-stu-id="f8cee-128">For a **seated-scale experience**, to let the user later recenter the seated origin, you can call the [XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) method:</span></span>

```cs
InputTracking.Recenter();
```

<span data-ttu-id="f8cee-129">Se si sta creando un'esperienza su larga [scala,](../../../../design/coordinate-systems.md)è possibile visualizzare di recente l'origine del mondo di Unity nella posizione head corrente dell'utente chiamando **[XR. Metodo InputTracking.Recenter.](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)**</span><span class="sxs-lookup"><span data-stu-id="f8cee-129">If you're building a [seated-scale experience](../../../../design/coordinate-systems.md), you can recenter Unity's world origin at the user's current head position by calling the **[XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** method.</span></span>