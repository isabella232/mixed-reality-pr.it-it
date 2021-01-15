---
title: Punto focale in Unity
description: Informazioni su come regolare manualmente la stabilità degli ologrammi in Unity impostando il punto di messa a fuoco per gli auricolari HoloLens e di realtà mista di Windows.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, punto focale, piano di messa a fuoco, piano di stabilizzazione, punto di stabilizzazione, riproiezione, LSR, buffer di profondità, auricolare realtà mista, auricolare della realtà mista di Windows, auricolare della realtà virtuale
ms.openlocfilehash: 2ceb5f2b58cbd1571b2d9f4de79acfe45779bfea
ms.sourcegitcommit: be7473bbebc1872d8c9df6f2da837efd3279dee6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/15/2021
ms.locfileid: "98226400"
---
# <a name="focus-point-in-unity"></a><span data-ttu-id="afac5-104">Punto focale in Unity</span><span class="sxs-lookup"><span data-stu-id="afac5-104">Focus point in Unity</span></span>

<span data-ttu-id="afac5-105">**Spazio dei nomi:** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="afac5-105">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="afac5-106">**Tipo**: *HolographicSettings*</span><span class="sxs-lookup"><span data-stu-id="afac5-106">**Type**: *HolographicSettings*</span></span>

<span data-ttu-id="afac5-107">Usare il [punto di interesse](../platform-capabilities-and-apis/hologram-stability.md#reprojection) per fornire a HoloLens un suggerimento su come stabilizzare al meglio gli ologrammi attualmente in fase di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="afac5-107">Use the [focus point](../platform-capabilities-and-apis/hologram-stability.md#reprojection) to provide HoloLens with a hint about how to best stabilize the holograms currently being displayed.</span></span>

<span data-ttu-id="afac5-108">Se si vuole impostare il punto di messa a fuoco in Unity, è necessario impostare ogni fotogramma usando *HolographicSettings. SetFocusPointForFrame ()*.</span><span class="sxs-lookup"><span data-stu-id="afac5-108">If you want to set the Focus Point in Unity, it needs to be set every frame using *HolographicSettings.SetFocusPointForFrame()*.</span></span> <span data-ttu-id="afac5-109">Quando il punto di attivazione non è impostato per un frame, viene usato il piano di stabilizzazione predefinito.</span><span class="sxs-lookup"><span data-stu-id="afac5-109">When the Focus Point isn't set for a frame, the default stabilization plane is used.</span></span>

> [!NOTE]
> <span data-ttu-id="afac5-110">Per impostazione predefinita, i nuovi progetti Unity hanno l'opzione "Abilita condivisione buffer di profondità" impostata.</span><span class="sxs-lookup"><span data-stu-id="afac5-110">By default, new Unity projects have the "Enable Depth Buffer Sharing" option set.</span></span>  <span data-ttu-id="afac5-111">Con questa opzione, un'app Unity in esecuzione in una cuffia desktop immersiva o un HoloLens che esegue l'aggiornamento di Windows 10 aprile 2018 (RS4) o versione successiva invierà il buffer di profondità a Windows per ottimizzare automaticamente la stabilità dell'ologramma, senza che l'app specifichi un punto di interesse:</span><span class="sxs-lookup"><span data-stu-id="afac5-111">With this option, a Unity app running on either an immersive desktop headset or a HoloLens running the Windows 10 April 2018 Update (RS4) or later will submit your depth buffer to Windows to optimize hologram stability automatically, without your app specifying a focus point:</span></span>
> * <span data-ttu-id="afac5-112">In un auricolare desktop immersivo, verrà abilitata la riproiezione basata sulla profondità per pixel.</span><span class="sxs-lookup"><span data-stu-id="afac5-112">On an immersive desktop headset, this will enable per-pixel depth-based reprojection.</span></span>
> * <span data-ttu-id="afac5-113">In una HoloLens che esegue l'aggiornamento di Windows 10 aprile 2018 o versione successiva, verrà analizzato il buffer di profondità per selezionare automaticamente un piano di stabilizzazione ottimale.</span><span class="sxs-lookup"><span data-stu-id="afac5-113">On a HoloLens running the Windows 10 April 2018 Update or later, this will analyze the depth buffer to pick an optimal stabilization plane automatically.</span></span>
>
> <span data-ttu-id="afac5-114">Entrambi gli approcci dovrebbero fornire una qualità dell'immagine ancora migliore senza lavoro esplicito da parte dell'app per selezionare un punto di interesse per ogni frame.</span><span class="sxs-lookup"><span data-stu-id="afac5-114">Either approach should provide even better image quality without explicit work by your app to select a focus point for each frame.</span></span>  <span data-ttu-id="afac5-115">Si noti che se si specifica un punto di interesse manualmente, che sostituisce il comportamento automatico descritto in precedenza, e in genere ridurrà la stabilità degli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="afac5-115">Note that if you do provide a focus point manually, that will override the automatic behavior described above, and will usually reduce hologram stability.</span></span>  <span data-ttu-id="afac5-116">In genere, è necessario specificare un punto di messa a fuoco manuale solo quando l'app è in esecuzione in un HoloLens che non è ancora stato aggiornato all'aggiornamento di Windows 10 aprile 2018.</span><span class="sxs-lookup"><span data-stu-id="afac5-116">Generally, you should only specify a manual focus point when your app is running on a HoloLens that has not yet been updated to the Windows 10 April 2018 Update.</span></span>

### <a name="example"></a><span data-ttu-id="afac5-117">Esempio</span><span class="sxs-lookup"><span data-stu-id="afac5-117">Example</span></span>

<span data-ttu-id="afac5-118">Esistono diversi modi per impostare il punto di interesse, come suggerito dagli overload disponibili nella funzione statica *SetFocusPointForFrame* .</span><span class="sxs-lookup"><span data-stu-id="afac5-118">There are many ways to set the Focus Point, as suggested by the overloads available on the *SetFocusPointForFrame* static function.</span></span> <span data-ttu-id="afac5-119">Di seguito è riportato un semplice esempio per impostare il piano di attivazione sull'oggetto fornito per ogni frame:</span><span class="sxs-lookup"><span data-stu-id="afac5-119">Presented below is a simple example to set the focus plane to the provided object for each frame:</span></span>

```cs
public GameObject focusedObject;
void Update()
{
    // Normally the normal is best set to be the opposite of the main camera's
    // forward vector.
    // If the content is actually all on a plane (like text), set the normal to
    // the normal of the plane and ensure the user does not pass through the
    // plane.
    var normal = -Camera.main.transform.forward;     
    var position = focusedObject.transform.position;
    UnityEngine.XR.WSA.HolographicSettings.SetFocusPointForFrame(position, normal);
}
```

> [!NOTE]
> <span data-ttu-id="afac5-120">Il semplice codice precedente può ridurre la stabilità dell'ologramma se l'oggetto con stato attivo termina dietro l'utente.</span><span class="sxs-lookup"><span data-stu-id="afac5-120">The simple code above may reduce hologram stability if the focused object ends up behind the user.</span></span> <span data-ttu-id="afac5-121">È in genere consigliabile impostare **[Abilita condivisione buffer di profondità](camera-in-unity.md#sharing-your-depth-buffers-with-windows)** anziché specificare manualmente un punto di interesse.</span><span class="sxs-lookup"><span data-stu-id="afac5-121">We generally recommend setting **[Enable Depth Buffer Sharing](camera-in-unity.md#sharing-your-depth-buffers-with-windows)** instead of manually specifying a focus point.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="afac5-122">Successivo checkpoint di sviluppo</span><span class="sxs-lookup"><span data-stu-id="afac5-122">Next Development Checkpoint</span></span>

<span data-ttu-id="afac5-123">Se si sta seguendo il percorso di sviluppo di Unity, è possibile esplorare le funzionalità e le API della piattaforma per la realtà mista.</span><span class="sxs-lookup"><span data-stu-id="afac5-123">If you're following the Unity development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="afac5-124">Da qui, è possibile passare all'argomento successivo:</span><span class="sxs-lookup"><span data-stu-id="afac5-124">From here, you can continue to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="afac5-125">Perdita del tracciamento</span><span class="sxs-lookup"><span data-stu-id="afac5-125">Tracking loss</span></span>](tracking-loss-in-unity.md)

<span data-ttu-id="afac5-126">In alternativa, passare direttamente alla distribuzione dell'app in un dispositivo o emulatore:</span><span class="sxs-lookup"><span data-stu-id="afac5-126">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="afac5-127">Eseguire la distribuzione in HoloLens o in modalità mista di Windows per la realtà mista</span><span class="sxs-lookup"><span data-stu-id="afac5-127">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)

<span data-ttu-id="afac5-128">È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#3-advanced-features) in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="afac5-128">You can always go back to the [Unity development checkpoints](unity-development-overview.md#3-advanced-features) at any time.</span></span>

### <a name="see-also"></a><span data-ttu-id="afac5-129">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="afac5-129">See also</span></span>

* [<span data-ttu-id="afac5-130">Piano di stabilizzazione</span><span class="sxs-lookup"><span data-stu-id="afac5-130">Stabilization plane</span></span>](../platform-capabilities-and-apis/hologram-stability.md#reprojection)
