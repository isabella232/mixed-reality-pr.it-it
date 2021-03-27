---
ms.openlocfilehash: 5f990569ae4052377cba717b5526bb8ba51b8016
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636382"
---
# <a name="mrtk"></a>[<span data-ttu-id="d5782-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="d5782-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="d5782-102">Usare la classe [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) di MRTK per Unity e impostare la **scala di destinazione** su uno **spazio** o su una **posizione**:</span><span class="sxs-lookup"><span data-stu-id="d5782-102">Use the [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) class from MRTK for Unity and set the **Target Scale** to either **Room** or **Standing**:</span></span>

![Finestra Impostazioni MRTK](../../images/mrtk-target-scale.png)

<span data-ttu-id="d5782-104">MRTK deve gestire automaticamente la posizione dei playspace e della fotocamera, ma è consigliabile eseguire il doppio controllo:</span><span class="sxs-lookup"><span data-stu-id="d5782-104">MRTK should handle the position of the playspace and camera automatically, but it's good to double check:</span></span>

![Playspace MRTK](../../images/mrtk-playspace.png)

1. <span data-ttu-id="d5782-106">Nel pannello **gerarchia** espandere il GameObject **MixedRealityPlayspace** e trovare l'oggetto figlio della **fotocamera principale**</span><span class="sxs-lookup"><span data-stu-id="d5782-106">From the **Hierarchy** panel, expand the **MixedRealityPlayspace** GameObject and find the **Main Camera** child object</span></span>
2. <span data-ttu-id="d5782-107">Nel pannello **Inspector** trovare il componente **Transform** e modificare la **posizione** in **(X: 0, Y: 0, Z: 0)**</span><span class="sxs-lookup"><span data-stu-id="d5782-107">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="d5782-108">SDK XR</span><span class="sxs-lookup"><span data-stu-id="d5782-108">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="d5782-109">Impostare la modalità di origine del rilevamento su [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span><span class="sxs-lookup"><span data-stu-id="d5782-109">Set your tracking origin mode on the [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span></span> <span data-ttu-id="d5782-110">Dopo aver ottenuto il sottosistema, chiamare [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span><span class="sxs-lookup"><span data-stu-id="d5782-110">After obtaining the subsystem, call [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span></span>

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Floor);
```

<span data-ttu-id="d5782-111">E collaborano con [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)di Unity.</span><span class="sxs-lookup"><span data-stu-id="d5782-111">And work with Unity's [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html).</span></span>

![Rig XR nella gerarchia](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="d5782-113">WSA legacy</span><span class="sxs-lookup"><span data-stu-id="d5782-113">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. <span data-ttu-id="d5782-114">Passare ad **altre impostazioni** sezione delle **impostazioni di Windows Store Player**</span><span class="sxs-lookup"><span data-stu-id="d5782-114">Go to **Other Settings** section of the **Windows Store Player Settings**</span></span>
2. <span data-ttu-id="d5782-115">Scegliere la **realtà mista di Windows** come dispositivo, che può essere elencato come **Windows olografico** nelle versioni precedenti di Unity</span><span class="sxs-lookup"><span data-stu-id="d5782-115">Choose **Windows Mixed Reality** as the device, which may be listed as **Windows Holographic** in older versions of Unity</span></span>
3. <span data-ttu-id="d5782-116">Selezione della **realtà virtuale supportata**</span><span class="sxs-lookup"><span data-stu-id="d5782-116">Select **Virtual Reality Supported**</span></span>

<span data-ttu-id="d5782-117">Poiché l'oggetto fotocamera principale viene contrassegnato automaticamente come fotocamera, Unity è in tutto lo spostamento e la traduzione.</span><span class="sxs-lookup"><span data-stu-id="d5782-117">Since the Main Camera object is automatically tagged as the camera, Unity powers all movement and translation.</span></span>

>[!NOTE]
><span data-ttu-id="d5782-118">Queste impostazioni devono essere applicate alla fotocamera in ogni scena dell'app.</span><span class="sxs-lookup"><span data-stu-id="d5782-118">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="d5782-119">Per impostazione predefinita, quando si crea una nuova scena in Unity, questa conterrà una fotocamera principale GameObject nella gerarchia che include il componente della fotocamera, ma le impostazioni non sono state applicate correttamente.</span><span class="sxs-lookup"><span data-stu-id="d5782-119">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but does not have the settings below properly applied.</span></span>

<span data-ttu-id="d5782-120">**Spazio dei nomi:** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="d5782-120">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="d5782-121">**Tipo:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="d5782-121">**Type:** *XRDevice*</span></span>

<span data-ttu-id="d5782-122">Per un'esperienza **di scalabilità o** **scalabilità**, è necessario inserire il contenuto relativo alla superficie.</span><span class="sxs-lookup"><span data-stu-id="d5782-122">For a **standing-scale** or **room-scale experience**, you'll need to place content relative to the floor.</span></span> <span data-ttu-id="d5782-123">Si ragiona sul pavimento dell'utente usando la **[fase spaziale](../../../../design/coordinate-systems.md#spatial-coordinate-systems)**, che rappresenta l'origine di livello del piano definita dall'utente e il limite di spazio facoltativo, configurato durante la prima esecuzione.</span><span class="sxs-lookup"><span data-stu-id="d5782-123">You reason about the user's floor using the **[spatial stage](../../../../design/coordinate-systems.md#spatial-coordinate-systems)**, which represents the user's defined floor-level origin and optional room boundary, set up during first run.</span></span>

<span data-ttu-id="d5782-124">Per assicurarsi che Unity stia operando con il sistema di coordinate globale a livello di piano, è possibile impostare e verificare che Unity usi il tipo di spazio di rilevamento RoomScale:</span><span class="sxs-lookup"><span data-stu-id="d5782-124">To ensure that Unity is operating with its world coordinate system at floor-level, you can set and test that Unity is using the RoomScale tracking space type:</span></span>

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```

* <span data-ttu-id="d5782-125">Se SetTrackingSpaceType restituisce true, Unity ha cambiato correttamente il sistema di coordinate globali per tenere traccia del [frame della fase di riferimento](../../../../design/coordinate-systems.md#spatial-coordinate-systems).</span><span class="sxs-lookup"><span data-stu-id="d5782-125">If SetTrackingSpaceType returns true, Unity has successfully switched its world coordinate system to track the [stage frame of reference](../../../../design/coordinate-systems.md#spatial-coordinate-systems).</span></span>
* <span data-ttu-id="d5782-126">Se SetTrackingSpaceType restituisce false, Unity non è stato in grado di passare al frame della fase di riferimento, probabilmente perché l'utente non ha configurato un piano nel proprio ambiente.</span><span class="sxs-lookup"><span data-stu-id="d5782-126">If SetTrackingSpaceType returns false, Unity was unable to switch to the stage frame of reference, likely because the user has not set up a floor in their environment.</span></span> <span data-ttu-id="d5782-127">Anche se un valore restituito false non è comune, può verificarsi se la fase è configurata in un'altra stanza e il dispositivo viene spostato nella stanza corrente senza che l'utente configurasse una nuova fase.</span><span class="sxs-lookup"><span data-stu-id="d5782-127">While a false return value isn't common, it can happen if the stage is set up in a different room and the device is moved to the current room without the user setting up a new stage.</span></span>

<span data-ttu-id="d5782-128">Quando l'app imposta correttamente il tipo di spazio di rilevamento RoomScale, il contenuto inserito sul piano y = 0 verrà visualizzato sul pavimento.</span><span class="sxs-lookup"><span data-stu-id="d5782-128">Once your app successfully sets the RoomScale tracking space type, content placed on the y=0 plane will appear on the floor.</span></span> <span data-ttu-id="d5782-129">L'origine a 0, 0, 0 corrisponderà alla posizione specifica del piano in cui l'utente si trovava durante l'installazione della stanza, con-Z che rappresenta la direzione in avanti durante l'installazione.</span><span class="sxs-lookup"><span data-stu-id="d5782-129">The origin at 0, 0, 0 will be the specific place on the floor where the user stood during room setup, with -Z representing the forward direction they were facing during setup.</span></span>