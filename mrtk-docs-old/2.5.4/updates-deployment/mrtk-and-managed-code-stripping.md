---
title: MRTK_and_managed_code_stripping
description: Stripping del codice in MRTK e Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 6b341f51b07da215269e3c3e0dee10ff151956b9d7e7b0c47e25fbbe9d4694c0
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115199783"
---
# <a name="mrtk-and-unity-managed-code-stripping"></a>Stripping del codice gestito MRTK e Unity

Quando si usa il back-end di scripting IL2CPP di Unity (facoltativo in Unity 2018.4, obbligatorio nella versione 2019 e nelle più recente), si verifica lo [stripping](https://docs.unity3d.com/Manual/ManagedCodeStripping.html) del codice gestito.
Il linker di Unity esegue questo processo per ridurre le dimensioni binarie e per ridurre i tempi di compilazione.

L'Toolkit realtà mista usa un file, , per influenzare il modo in cui il linker di Unity elabora `link.xml` gli assembly MRTK. Questo file, descritto in modo completo nella documentazione di Unity, fornisce al linker istruzioni su come mantenere il codice quando non è possibile dedurne [l'utilizzo](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML)(ad esempio, usato tramite reflection).

Come piattaforma flessibile e personalizzabile, MRTK crea il file in durante l'importazione, se non `link.xml` `Assets/MixedRealityToolkit.Generated` esiste. I file di link.xml non vengono sovrascritti. È consigliabile aggiungere `link.xml` e al controllo della `link.xml.meta` versione. Gli sviluppatori devono essere in grado di `Assets/MixedRealityToolkit.Generated/link.xml` personalizzare per soddisfare le esigenze del progetto.

Per impostazione predefinita, link.xml file creato da MRTK mantiene l'intero assembly mostrato nei dati seguenti.

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

Per altre informazioni sul formato link.xml file, vedere la documentazione di Unity.

## <a name="see-also"></a>Vedi anche

- [Unity: stripping del codice gestito](https://docs.unity3d.com/Manual/ManagedCodeStripping.html)
- [Unity: collegare un file XML](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML)
