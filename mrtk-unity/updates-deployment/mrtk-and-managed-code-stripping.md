---
title: MRTK e stripping del codice gestito
description: Stripping del codice in MRTK e Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 09e5140fd9585c19eacac5ba937eaf4ea8f2a8ea
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143736"
---
# <a name="mrtk-and-unity-managed-code-stripping"></a><span data-ttu-id="3fafe-104">Stripping del codice gestito MRTK e Unity</span><span class="sxs-lookup"><span data-stu-id="3fafe-104">MRTK and Unity managed code stripping</span></span>

<span data-ttu-id="3fafe-105">Quando si usa il back-end di scripting IL2CPP di Unity (facoltativo in Unity 2018.4, obbligatorio nella versione 2019 e nelle più recente), si verifica lo [stripping](https://docs.unity3d.com/Manual/ManagedCodeStripping.html) del codice gestito.</span><span class="sxs-lookup"><span data-stu-id="3fafe-105">When using Unity's IL2CPP scripting backend (optional in Unity 2018.4, required in 2019 and newer), [managed code stripping](https://docs.unity3d.com/Manual/ManagedCodeStripping.html) occurs.</span></span>
<span data-ttu-id="3fafe-106">Il linker di Unity esegue questo processo per ridurre le dimensioni binarie e per ridurre i tempi di compilazione.</span><span class="sxs-lookup"><span data-stu-id="3fafe-106">Unity's linker performs this process to reduce binary size as well as to decrease build times.</span></span>

<span data-ttu-id="3fafe-107">Mixed Reality Toolkit usa un file, , per influenzare il modo in cui il linker di `link.xml` Unity elabora gli assembly MRTK.</span><span class="sxs-lookup"><span data-stu-id="3fafe-107">The Mixed Reality Toolkit uses a file, `link.xml`, to influence how Unity's linker processes MRTK assemblies.</span></span> <span data-ttu-id="3fafe-108">Questo file, descritto in modo completo nella documentazione di Unity, fornisce al linker istruzioni su come mantenere il codice quando non è possibile dedurne [l'utilizzo](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML)(ad esempio, usato tramite reflection).</span><span class="sxs-lookup"><span data-stu-id="3fafe-108">This file, described in full in [Unity's documentation](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML), provides the linker with instructions on how to preserve code when its usage cannot be inferred (ex: used via reflection).</span></span>

<span data-ttu-id="3fafe-109">Come piattaforma flessibile e personalizzabile, MRTK crea il file in durante l'importazione, se non `link.xml` `Assets/MixedRealityToolkit.Generated` esiste.</span><span class="sxs-lookup"><span data-stu-id="3fafe-109">As a flexible and customizable platform, MRTK creates the `link.xml` file in `Assets/MixedRealityToolkit.Generated` on import, if it is found to not exist.</span></span> <span data-ttu-id="3fafe-110">I file di link.xml non vengono sovrascritti.</span><span class="sxs-lookup"><span data-stu-id="3fafe-110">Pre-existing link.xml files are not overwritten.</span></span> <span data-ttu-id="3fafe-111">È consigliabile aggiungere `link.xml` e al controllo della `link.xml.meta` versione.</span><span class="sxs-lookup"><span data-stu-id="3fafe-111">It is recommended that `link.xml` and `link.xml.meta` be added to version control.</span></span> <span data-ttu-id="3fafe-112">Gli sviluppatori devono essere in grado di `Assets/MixedRealityToolkit.Generated/link.xml` personalizzare per soddisfare le esigenze del progetto.</span><span class="sxs-lookup"><span data-stu-id="3fafe-112">Developers should feel free to customize `Assets/MixedRealityToolkit.Generated/link.xml` to meet the needs of the project.</span></span>

<span data-ttu-id="3fafe-113">Per impostazione predefinita, link.xml file creato da MRTK mantiene l'intero assembly mostrato nei dati seguenti.</span><span class="sxs-lookup"><span data-stu-id="3fafe-113">By default, the link.xml file created by MRTK preserves the entirety of the assemblies shown in the following data.</span></span>

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

<span data-ttu-id="3fafe-114">Per altre informazioni sul formato link.xml file, vedere la documentazione di Unity.</span><span class="sxs-lookup"><span data-stu-id="3fafe-114">For more information on the link.xml file format, please refer to the Unity documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="3fafe-115">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="3fafe-115">See also</span></span>

- [<span data-ttu-id="3fafe-116">Unity: stripping del codice gestito</span><span class="sxs-lookup"><span data-stu-id="3fafe-116">Unity: Managed Code Stripping</span></span>](https://docs.unity3d.com/Manual/ManagedCodeStripping.html)
- [<span data-ttu-id="3fafe-117">Unity: collegare un file XML</span><span class="sxs-lookup"><span data-stu-id="3fafe-117">Unity: Link XML file</span></span>](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML)
