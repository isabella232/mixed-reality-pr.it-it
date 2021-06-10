---
ms.openlocfilehash: 61fe8754192c1fbd0634fd9d1e1994327599321b
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748517"
---
# <a name="mrtk"></a>[<span data-ttu-id="af78d-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="af78d-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="af78d-102">Usare la [classe MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) di MRTK per Unity e impostare **La** scala di destinazione su **Room** o **Standing**:</span><span class="sxs-lookup"><span data-stu-id="af78d-102">Use the [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) class from MRTK for Unity and set the **Target Scale** to either **Room** or **Standing**:</span></span>

![Finestra delle impostazioni MRTK](../../images/mrtk-target-scale.png)

<span data-ttu-id="af78d-104">MRTK deve gestire automaticamente la posizione dello spazio di riproduzione e della fotocamera, ma è consigliabile eseguire un doppio controllo:</span><span class="sxs-lookup"><span data-stu-id="af78d-104">MRTK should handle the position of the playspace and camera automatically, but it's good to double check:</span></span>

![Spazio di riproduzione MRTK](../../images/mrtk-playspace.png)

1. <span data-ttu-id="af78d-106">Nel pannello **Gerarchia** espandere **MixedRealityPlayspace** GameObject e trovare l'oggetto **figlio Main Camera**</span><span class="sxs-lookup"><span data-stu-id="af78d-106">From the **Hierarchy** panel, expand the **MixedRealityPlayspace** GameObject and find the **Main Camera** child object</span></span>
2. <span data-ttu-id="af78d-107">Nel pannello **Inspector** (Controllo) trovare **il componente Transform** (Trasforma) e impostare Position **(Posizione)** su **(X: 0, Y: 0, Z: 0)**</span><span class="sxs-lookup"><span data-stu-id="af78d-107">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="af78d-108">XR SDK</span><span class="sxs-lookup"><span data-stu-id="af78d-108">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="af78d-109">Impostare la modalità di origine di rilevamento in [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span><span class="sxs-lookup"><span data-stu-id="af78d-109">Set your tracking origin mode on the [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span></span> <span data-ttu-id="af78d-110">Dopo aver ottenuto il sottosistema, chiamare [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span><span class="sxs-lookup"><span data-stu-id="af78d-110">After obtaining the subsystem, call [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span></span>

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Floor);
```

<span data-ttu-id="af78d-111">E usare [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)di Unity.</span><span class="sxs-lookup"><span data-stu-id="af78d-111">And work with Unity's [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html).</span></span>

![Rig XR nella gerarchia](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="af78d-113">Legacy WSA</span><span class="sxs-lookup"><span data-stu-id="af78d-113">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. <span data-ttu-id="af78d-114">Passare alla **sezione Altre impostazioni** delle impostazioni di Windows Store **Player**</span><span class="sxs-lookup"><span data-stu-id="af78d-114">Go to **Other Settings** section of the **Windows Store Player Settings**</span></span>
2. <span data-ttu-id="af78d-115">Scegliere **Windows Mixed Reality** come dispositivo, che potrebbe essere elencato come **Windows Holographic** nelle versioni precedenti di Unity</span><span class="sxs-lookup"><span data-stu-id="af78d-115">Choose **Windows Mixed Reality** as the device, which may be listed as **Windows Holographic** in older versions of Unity</span></span>
3. <span data-ttu-id="af78d-116">Selezionare **Realtà virtuale supportata**</span><span class="sxs-lookup"><span data-stu-id="af78d-116">Select **Virtual Reality Supported**</span></span>

<span data-ttu-id="af78d-117">Poiché l'oggetto Fotocamera principale viene contrassegnato automaticamente come fotocamera, Unity alimenta tutti i movimenti e la traduzione.</span><span class="sxs-lookup"><span data-stu-id="af78d-117">Since the Main Camera object is automatically tagged as the camera, Unity powers all movement and translation.</span></span>

>[!NOTE]
><span data-ttu-id="af78d-118">Queste impostazioni devono essere applicate alla fotocamera in ogni scena dell'app.</span><span class="sxs-lookup"><span data-stu-id="af78d-118">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="af78d-119">Per impostazione predefinita, quando si crea una nuova scena in Unity, questa conterrà un oggetto GameObject della fotocamera principale nella gerarchia che include il componente Fotocamera, ma non avrà le impostazioni seguenti applicate correttamente.</span><span class="sxs-lookup"><span data-stu-id="af78d-119">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but does not have the settings below properly applied.</span></span>

<span data-ttu-id="af78d-120">**Spazio dei nomi:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="af78d-120">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="af78d-121">**Tipo:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="af78d-121">**Type:** *XRDevice*</span></span>

<span data-ttu-id="af78d-122">Per **un'esperienza su larga** **scala** o su scala locale, è necessario posizionare il contenuto rispetto al piano.</span><span class="sxs-lookup"><span data-stu-id="af78d-122">For a **standing-scale** or **room-scale experience**, you'll need to place content relative to the floor.</span></span> <span data-ttu-id="af78d-123">Il piano dell'utente viene ragione usando la fase spaziale **[,](../../../../design/coordinate-systems.md#spatial-coordinate-systems)** che rappresenta l'origine definita a livello di piano dell'utente e il limite facoltativo della stanza, configurato durante la prima esecuzione.</span><span class="sxs-lookup"><span data-stu-id="af78d-123">You reason about the user's floor using the **[spatial stage](../../../../design/coordinate-systems.md#spatial-coordinate-systems)**, which represents the user's defined floor-level origin and optional room boundary, set up during first run.</span></span>

<span data-ttu-id="af78d-124">Per garantire il funzionamento di Unity con il sistema di coordinate globale a livello di piano, è possibile impostare e testare che Unity sta usando il tipo di spazio di rilevamento RoomScale:</span><span class="sxs-lookup"><span data-stu-id="af78d-124">To ensure that Unity is operating with its world coordinate system at floor-level, you can set and test that Unity is using the RoomScale tracking space type:</span></span>

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

* <span data-ttu-id="af78d-125">Se SetTrackingSpaceType restituisce true, Unity ha commutato correttamente il sistema di coordinate del mondo per tenere traccia del [fotogramma della fase di riferimento.](../../../../design/coordinate-systems.md#spatial-coordinate-systems)</span><span class="sxs-lookup"><span data-stu-id="af78d-125">If SetTrackingSpaceType returns true, Unity has successfully switched its world coordinate system to track the [stage frame of reference](../../../../design/coordinate-systems.md#spatial-coordinate-systems).</span></span>
* <span data-ttu-id="af78d-126">Se SetTrackingSpaceType restituisce false, Unity non è stato in grado di passare al frame di fase di riferimento, probabilmente perché l'utente non ha configurato un piano nel proprio ambiente.</span><span class="sxs-lookup"><span data-stu-id="af78d-126">If SetTrackingSpaceType returns false, Unity was unable to switch to the stage frame of reference, likely because the user has not set up a floor in their environment.</span></span> <span data-ttu-id="af78d-127">Anche se un valore restituito falso non è comune, può verificarsi se la fase è impostata in una stanza diversa e il dispositivo viene spostato nella stanza corrente senza che l'utente configura una nuova fase.</span><span class="sxs-lookup"><span data-stu-id="af78d-127">While a false return value isn't common, it can happen if the stage is set up in a different room and the device is moved to the current room without the user setting up a new stage.</span></span>

<span data-ttu-id="af78d-128">Dopo che l'app ha impostato correttamente il tipo di spazio di rilevamento RoomScale, sul piano y=0 verrà visualizzato il contenuto posizionato sul piano y=0.</span><span class="sxs-lookup"><span data-stu-id="af78d-128">Once your app successfully sets the RoomScale tracking space type, content placed on the y=0 plane will appear on the floor.</span></span> <span data-ttu-id="af78d-129">L'origine a 0, 0, 0 sarà la posizione specifica sul piano in cui si trovava l'utente durante la configurazione della stanza, con -Z che rappresenta la direzione in avanti che stava affrontando durante la configurazione.</span><span class="sxs-lookup"><span data-stu-id="af78d-129">The origin at 0, 0, 0 will be the specific place on the floor where the user stood during room setup, with -Z representing the forward direction they were facing during setup.</span></span>