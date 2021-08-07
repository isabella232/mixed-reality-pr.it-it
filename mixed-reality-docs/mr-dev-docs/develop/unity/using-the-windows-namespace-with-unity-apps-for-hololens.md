---
title: API WinRT con Unity per HoloLens
description: Informazioni su come usare le API WinRT e lo spazio dei nomi Windows nei progetti di realtà mista Unity per HoloLens.
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, WinRT, windows mixed reality, API, procedura dettagliata, visore VR di realtà mista, visore VR di realtà mista windows, visore VR di realtà virtuale, API di realtà mista
ms.openlocfilehash: 158c28d9186269108442226bbfcfc90a3c235a71336fdab9dbf9eadc21a309a1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115215607"
---
# <a name="winrt-apis-with-unity-for-hololens"></a>API WinRT con Unity per HoloLens

Questa pagina descrive come usare le API WinRT nel progetto Unity per HoloLens.

## <a name="mixed-reality-apis"></a>API di realtà mista

Un subset incentrato sulla realtà mista di Windows SDK è stato reso disponibile in una proiezione compatibile con .NET Standard 2.0, che è possibile usare nel progetto senza direttive per il preprocessore. La maggior parte delle API nel Windows. Percezione e Windows. Ui. Gli spazi dei nomi Input.Spatial sono inclusi e possono espandersi per includere API aggiuntive in futuro. Le API proiettate possono essere usate durante l'esecuzione nell'editor, che consente l'uso della [modalità di riproduzione](/windows/mixed-reality/unity-play-mode). Per usare questa proiezione, apportare le modifiche seguenti al progetto:

1) Aggiungere un riferimento al [file Microsoft.Windows. MixedReality.DotNetWinRT NuGet](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) pacchetto [usando NuGet per Unity.](https://github.com/GlitchEnzo/NuGetForUnity)
2) Aggiungere come prefisso i riferimenti allo `Windows` spazio dei nomi con `Microsoft.` :
```cs
using namespace Microsoft.Windows.Perception.Spatial;
```
3) Sostituire i cast dei puntatori nativi con `FromNativePtr` :
```cs
var worldOrigin = SpatialCoordinateSystem.FromNativePtr(unityWorldOriginPtr);
```

## <a name="conditionally-include-winrt-api-calls"></a>Includere in modo condizionale le chiamate API WinRT

Puoi anche usare le API WinRT nei progetti Unity compilati per la piattaforma universal Windows e la piattaforma Xbox One usando direttive per il preprocessore. Qualsiasi codice scritto in script Unity che hanno come destinazione le API WinRT deve essere incluso in modo condizionale solo per tali compilazioni. 

Questa operazione può essere eseguita tramite due passaggi in Unity:
1) Il livello di compatibilità api deve essere impostato su **.NET 4.6** o **.NET Standard 2.0 nelle** impostazioni del lettore
    - **Modifica**  >  **Project Impostazioni**  >  **Lettore**  >  **Configurazione**  >  **Livello di compatibilità API** **per .NET 4.6** **o .NET Standard 2.0**
2) La direttiva per il **preprocessore ENABLE_WINMD_SUPPORT** deve essere racchiusa in qualsiasi codice basato su WinRT

Il frammento di codice seguente è disponibile nella pagina manuale di Unity per [Universal Windows Platform: API WinRT negli script C#.](https://docs.unity3d.com/Manual/windowsstore-scripts.html) In questo esempio viene restituito un ID pubblicitario, ma solo in UWP e Xbox One compilazioni:

```
using UnityEngine;
public class WinRTAPI : MonoBehaviour {
    void Update() {
        auto adId = GetAdvertisingId();
        // ...
    }

    string GetAdvertisingId() {
        #if ENABLE_WINMD_SUPPORT
            return Windows.System.UserProfile.AdvertisingManager.AdvertisingId;
        #else
            return "";
        #endif
    }
}
```

## <a name="edit-your-scripts-in-a-unity-c-project"></a>Modificare gli script in un progetto C# unity

Quando si fa doppio clic su uno script nell'editor di Unity, per impostazione predefinita lo script viene avviato in un progetto editor. Le API WinRT appariranno sconosciute perché il progetto Visual Studio non fa riferimento al runtime Windows runtime. La **ENABLE_WINMD_SUPPORT** è indefinita  e qualsiasi codice #if di cui è stato eseguito il wrapping viene ignorato fino a quando non si compila il progetto in una soluzione Visual Studio UWP.

## <a name="see-also"></a>Vedi anche
* [Esportazione e creazione di una soluzione di Visual Studio Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Windows Supporto di runtime in Unity](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)