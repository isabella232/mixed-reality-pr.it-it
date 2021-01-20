---
title: API WinRT con Unity per HoloLens
description: Come usare le API WinRT e lo spazio dei nomi di Windows nei progetti di realtà mista Unity per HoloLens.
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, WinRT, realtà mista di Windows, API, procedura dettagliata, cuffie per la realtà mista, auricolare di realtà mista, auricolare di realtà virtuale, API di realtà mista
ms.openlocfilehash: 2116f0025449fdf127998e605f87de456e9bdaf9
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583550"
---
# <a name="winrt-apis-with-unity-for-hololens"></a>API WinRT con Unity per HoloLens

Questa pagina descrive come usare le API WinRT nel progetto Unity per HoloLens.

## <a name="mixed-reality-apis"></a>API di realtà mista

Un subset incentrato sulla realtà mista del Windows SDK è stato reso disponibile in una proiezione compatibile .NET Standard 2,0, che è possibile usare nel progetto senza direttive per il preprocessore. La maggior parte delle API nelle finestre. Gli spazi dei nomi di percezione e Windows. UI. input. Spatial sono inclusi e possono espandersi per includere altre API in futuro. Le API proiettate possono essere usate durante l'esecuzione nell'editor, che consente l'uso della [modalità di riproduzione](//windows/mixed-reality/unity-play-mode). Per usare questa proiezione, apportare le modifiche seguenti al progetto:

1) Aggiungere un riferimento al pacchetto NuGet [Microsoft. Windows. MixedReality. DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) usando [NuGet per Unity](https://github.com/GlitchEnzo/NuGetForUnity).
2) Prefisso riferimenti allo `Windows` spazio dei nomi con `Microsoft.` :
```cs
using namespace Microsoft.Windows.Perception.Spatial;
```
3) Sostituire i cast puntatore nativi con `FromNativePtr` :
```cs
var worldOrigin = SpatialCoordinateSystem.FromNativePtr(unityWorldOriginPtr);
```

## <a name="conditionally-include-winrt-api-calls"></a>Includere in modo condizionale le chiamate all'API WinRT

È anche possibile usare le API WinRT nei progetti Unity compilati per la piattaforma piattaforma UWP (Universal Windows Platform) e Xbox One usando le direttive per il preprocessore. Qualsiasi codice scritto negli script Unity destinati alle API WinRT deve essere incluso in modo condizionale solo per le compilazioni. 

Questa operazione può essere eseguita con due passaggi in Unity:
1) Il livello di compatibilità API deve essere impostato su **.net 4,6** o **.NET standard 2,0** nelle impostazioni del lettore
    - **Modifica**  >  **Impostazioni progetto**  >  **Lettore**  >  di **Configurazione**  >  di **Livello di compatibilità API** per **.net 4,6** o **.NET standard 2,0**
2) La direttiva per il preprocessore **ENABLE_WINMD_SUPPORT** deve essere racchiusa tra qualsiasi codice sfruttato in WinRT

Il frammento di codice seguente si trova nella pagina manuale di Unity per [piattaforma UWP (Universal Windows Platform): API WinRT negli script C#](https://docs.unity3d.com/Manual/windowsstore-scripts.html). In questo esempio viene restituito un ID pubblicitario, ma solo in UWP e Xbox One viene compilata:

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

## <a name="edit-your-scripts-in-a-unity-c-project"></a>Modificare gli script in un progetto C# Unity

Quando si fa doppio clic su uno script nell'editor di Unity, viene avviato per impostazione predefinita lo script in un progetto di editor. Le API di WinRT sembreranno sconosciute perché il progetto di Visual Studio non fa riferimento al Windows Runtime. La direttiva **ENABLE_WINMD_SUPPORT** non è definita e qualsiasi codice *#if* con wrapper viene ignorato finché il progetto non viene compilato in una soluzione UWP di Visual Studio.

## <a name="see-also"></a>Vedere anche
* [Esportazione e creazione di una soluzione di Visual Studio Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Unity support Windows Runtime](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)