---
title: MRTK_and_managed_code_stripping
description: Rimozione del codice in MRTK e Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 7e80f25f6e5af7fe851bf9106ebbd07dece5dbad
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104681574"
---
# <a name="mrtk-and-unity-managed-code-stripping"></a><span data-ttu-id="fa3f6-104">Rimozione del codice gestito di MRTK e Unity</span><span class="sxs-lookup"><span data-stu-id="fa3f6-104">MRTK and Unity managed code stripping</span></span>

<span data-ttu-id="fa3f6-105">Quando si usa il back-end di scripting IL2CPP di Unity (facoltativo in Unity 2018,4, richiesto in 2019 e versioni successive), si verifica la [rimozione del codice gestito](https://docs.unity3d.com/Manual/ManagedCodeStripping.html) .</span><span class="sxs-lookup"><span data-stu-id="fa3f6-105">When using Unity's IL2CPP scripting backend (optional in Unity 2018.4, required in 2019 and newer), [managed code stripping](https://docs.unity3d.com/Manual/ManagedCodeStripping.html) occurs.</span></span>
<span data-ttu-id="fa3f6-106">Il linker di Unity esegue questo processo per ridurre le dimensioni binarie e per ridurre i tempi di compilazione.</span><span class="sxs-lookup"><span data-stu-id="fa3f6-106">Unity's linker performs this process to reduce binary size as well as to decrease build times.</span></span>

<span data-ttu-id="fa3f6-107">Il Toolkit di realtà mista Usa un file, `link.xml` , per influenzare il modo in cui il linker di Unity elabora gli assembly MRTK.</span><span class="sxs-lookup"><span data-stu-id="fa3f6-107">The Mixed Reality Toolkit uses a file, `link.xml`, to influence how Unity's linker processes MRTK assemblies.</span></span> <span data-ttu-id="fa3f6-108">Questo file, descritto nella documentazione completa di [Unity](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML), fornisce al linker istruzioni su come mantenere il codice quando non è possibile dedurre l'utilizzo (ad esempio, usato tramite Reflection).</span><span class="sxs-lookup"><span data-stu-id="fa3f6-108">This file, described in full in [Unity's documentation](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML), provides the linker with instructions on how to preserve code when its usage cannot be inferred (ex: used via reflection).</span></span>

<span data-ttu-id="fa3f6-109">Come piattaforma flessibile e personalizzabile, MRTK crea il `link.xml` file in in `Assets/MixedRealityToolkit.Generated` caso di importazione, se non è presente.</span><span class="sxs-lookup"><span data-stu-id="fa3f6-109">As a flexible and customizable platform, MRTK creates the `link.xml` file in `Assets/MixedRealityToolkit.Generated` on import, if it is found to not exist.</span></span> <span data-ttu-id="fa3f6-110">I file di link.xml preesistenti non vengono sovrascritti.</span><span class="sxs-lookup"><span data-stu-id="fa3f6-110">Pre-existing link.xml files are not overwritten.</span></span> <span data-ttu-id="fa3f6-111">È consigliabile `link.xml` `link.xml.meta` aggiungere e al controllo della versione.</span><span class="sxs-lookup"><span data-stu-id="fa3f6-111">It is recommended that `link.xml` and `link.xml.meta` be added to version control.</span></span> <span data-ttu-id="fa3f6-112">Gli sviluppatori devono essere in grado di personalizzare `Assets/MixedRealityToolkit.Generated/link.xml` per soddisfare le esigenze del progetto.</span><span class="sxs-lookup"><span data-stu-id="fa3f6-112">Developers should feel free to customize `Assets/MixedRealityToolkit.Generated/link.xml` to meet the needs of the project.</span></span>

<span data-ttu-id="fa3f6-113">Per impostazione predefinita, il file link.xml creato da MRTK conserva l'intero assembly illustrato nei dati seguenti.</span><span class="sxs-lookup"><span data-stu-id="fa3f6-113">By default, the link.xml file created by MRTK preserves the entirety of the assemblies shown in the following data.</span></span>

``` xml
<linker> 
  <!-- 
    This link.xml file is provided to prevent MRTK code from being optimized away 
    during IL2CPP builds.More details on when this is needed and why this is needed 
    can be found here: https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5273 
    If your application doesn't use some specific services (for example, if teleportation system is 
    disabled in the profile), it is possible to remove their corresponding lines down 
    below(in the previous example, we would remove the TeleportSystem below). 
    It's recommended to start with this list and narrow down if you want to ensure 
    specific bits of code get optimized away. 
  --> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.SDK" preserve="all"/> 
  <!-- Core systems --> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.BoundarySystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.CameraSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.DiagnosticsSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.InputSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.SceneSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.SpatialAwarenessSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.TeleportSystem" preserve="all"/> 
  <!-- Data providers --> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.LeapMotion" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenVR" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.UnityAR" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.WindowsMixedReality.Shared" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.WindowsMixedReality" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.XRSDK.WindowsMixedReality" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.WindowsVoiceInput" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.XRSDK" preserve="all"/> 
  <!-- Extension services --> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Extensions.HandPhysics" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Extensions.Tracking" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Extensions.SceneTransitionService" preserve="all"/> 
</linker>
```

<span data-ttu-id="fa3f6-114">Per ulteriori informazioni sul formato di file link.xml, consultare la documentazione di Unity.</span><span class="sxs-lookup"><span data-stu-id="fa3f6-114">For more information on the link.xml file format, please refer to the Unity documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="fa3f6-115">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="fa3f6-115">See also</span></span>

- [<span data-ttu-id="fa3f6-116">Unity: rimozione di codice gestito</span><span class="sxs-lookup"><span data-stu-id="fa3f6-116">Unity: Managed Code Stripping</span></span>](https://docs.unity3d.com/Manual/ManagedCodeStripping.html)
- [<span data-ttu-id="fa3f6-117">Unity: collega file XML</span><span class="sxs-lookup"><span data-stu-id="fa3f6-117">Unity: Link XML file</span></span>](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML)
