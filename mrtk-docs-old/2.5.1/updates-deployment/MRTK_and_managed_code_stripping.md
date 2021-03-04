---
title: MRTK_and_managed_code_stripping
description: Rimozione del codice in MRTK e Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: eaae57db83e2870f65f8febb2f46fa763b357716
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782434"
---
# <a name="mrtk-and-unity-managed-code-stripping"></a>Rimozione del codice gestito di MRTK e Unity

Quando si usa il back-end di scripting IL2CPP di Unity (facoltativo in Unity 2018,4, richiesto in 2019 e versioni successive), si verifica la [rimozione del codice gestito](https://docs.unity3d.com/Manual/ManagedCodeStripping.html) .
Il linker di Unity esegue questo processo per ridurre le dimensioni binarie e per ridurre i tempi di compilazione.

Il Toolkit di realtà mista Usa un file, `link.xml` , per influenzare il modo in cui il linker di Unity elabora gli assembly MRTK. Questo file, descritto nella documentazione completa di [Unity](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML), fornisce al linker istruzioni su come mantenere il codice quando non è possibile dedurre l'utilizzo (ad esempio, usato tramite Reflection).

Come piattaforma flessibile e personalizzabile, MRTK crea il `link.xml` file in in `Assets/MixedRealityToolkit.Generated` caso di importazione, se non è presente. I file di link.xml preesistenti non vengono sovrascritti. È consigliabile `link.xml` `link.xml.meta` aggiungere e al controllo della versione. Gli sviluppatori devono essere in grado di personalizzare `Assets/MixedRealityToolkit.Generated/link.xml` per soddisfare le esigenze del progetto.

Per impostazione predefinita, il file link.xml creato da MRTK conserva l'intero assembly illustrato nei dati seguenti.

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

Per ulteriori informazioni sul formato di file link.xml, consultare la documentazione di Unity.

## <a name="see-also"></a>Vedi anche

- [Unity: rimozione di codice gestito](https://docs.unity3d.com/Manual/ManagedCodeStripping.html)
- [Unity: collega file XML](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML)
