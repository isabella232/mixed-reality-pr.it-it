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
# <a name="winrt-apis-with-unity-for-hololens"></a><span data-ttu-id="2605c-104">API WinRT con Unity per HoloLens</span><span class="sxs-lookup"><span data-stu-id="2605c-104">WinRT APIs with Unity for HoloLens</span></span>

<span data-ttu-id="2605c-105">Questa pagina descrive come usare le API WinRT nel progetto Unity per HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2605c-105">This page describes how to make use of WinRT APIs in your Unity project for HoloLens.</span></span>

## <a name="mixed-reality-apis"></a><span data-ttu-id="2605c-106">API di realtà mista</span><span class="sxs-lookup"><span data-stu-id="2605c-106">Mixed Reality APIs</span></span>

<span data-ttu-id="2605c-107">Un subset incentrato sulla realtà mista del Windows SDK è stato reso disponibile in una proiezione compatibile .NET Standard 2,0, che è possibile usare nel progetto senza direttive per il preprocessore.</span><span class="sxs-lookup"><span data-stu-id="2605c-107">A Mixed Reality focused subset of the Windows SDK has been made available in a .NET Standard 2.0 compatible projection, which you can use in your project without preprocessor directives.</span></span> <span data-ttu-id="2605c-108">La maggior parte delle API nelle finestre.</span><span class="sxs-lookup"><span data-stu-id="2605c-108">Most APIs in the Windows.</span></span> <span data-ttu-id="2605c-109">Gli spazi dei nomi di percezione e Windows. UI. input. Spatial sono inclusi e possono espandersi per includere altre API in futuro.</span><span class="sxs-lookup"><span data-stu-id="2605c-109">Perception and Windows.UI.Input.Spatial namespaces are included and may expand to include additional APIs in the future.</span></span> <span data-ttu-id="2605c-110">Le API proiettate possono essere usate durante l'esecuzione nell'editor, che consente l'uso della [modalità di riproduzione](//windows/mixed-reality/unity-play-mode).</span><span class="sxs-lookup"><span data-stu-id="2605c-110">The projected APIs can be used while running in the Editor, which enables the use of [Play Mode](//windows/mixed-reality/unity-play-mode).</span></span> <span data-ttu-id="2605c-111">Per usare questa proiezione, apportare le modifiche seguenti al progetto:</span><span class="sxs-lookup"><span data-stu-id="2605c-111">To use this projection, make the following modifications to your project:</span></span>

1) <span data-ttu-id="2605c-112">Aggiungere un riferimento al pacchetto NuGet [Microsoft. Windows. MixedReality. DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) usando [NuGet per Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span><span class="sxs-lookup"><span data-stu-id="2605c-112">Add a reference to the [Microsoft.Windows.MixedReality.DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) NuGet package using [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span></span>
2) <span data-ttu-id="2605c-113">Prefisso riferimenti allo `Windows` spazio dei nomi con `Microsoft.` :</span><span class="sxs-lookup"><span data-stu-id="2605c-113">Prefix references to the `Windows` namespace with `Microsoft.`:</span></span>
```cs
using namespace Microsoft.Windows.Perception.Spatial;
```
3) <span data-ttu-id="2605c-114">Sostituire i cast puntatore nativi con `FromNativePtr` :</span><span class="sxs-lookup"><span data-stu-id="2605c-114">Replace native pointer casts with `FromNativePtr`:</span></span>
```cs
var worldOrigin = SpatialCoordinateSystem.FromNativePtr(unityWorldOriginPtr);
```

## <a name="conditionally-include-winrt-api-calls"></a><span data-ttu-id="2605c-115">Includere in modo condizionale le chiamate all'API WinRT</span><span class="sxs-lookup"><span data-stu-id="2605c-115">Conditionally include WinRT API calls</span></span>

<span data-ttu-id="2605c-116">È anche possibile usare le API WinRT nei progetti Unity compilati per la piattaforma piattaforma UWP (Universal Windows Platform) e Xbox One usando le direttive per il preprocessore.</span><span class="sxs-lookup"><span data-stu-id="2605c-116">You can also use the WinRT APIs in Unity projects built for the Universal Windows Platform and Xbox One platform by using preprocessor directives.</span></span> <span data-ttu-id="2605c-117">Qualsiasi codice scritto negli script Unity destinati alle API WinRT deve essere incluso in modo condizionale solo per le compilazioni.</span><span class="sxs-lookup"><span data-stu-id="2605c-117">Any code that you write in Unity scripts that target WinRT APIs must be conditionally included for only those builds.</span></span> 

<span data-ttu-id="2605c-118">Questa operazione può essere eseguita con due passaggi in Unity:</span><span class="sxs-lookup"><span data-stu-id="2605c-118">This can be done via two steps in Unity:</span></span>
1) <span data-ttu-id="2605c-119">Il livello di compatibilità API deve essere impostato su **.net 4,6** o **.NET standard 2,0** nelle impostazioni del lettore</span><span class="sxs-lookup"><span data-stu-id="2605c-119">API compatibility level must be set to **.NET 4.6** or **.NET Standard 2.0** in the player settings</span></span>
    - <span data-ttu-id="2605c-120">**Modifica**  >  **Impostazioni progetto**  >  **Lettore**  >  di **Configurazione**  >  di **Livello di compatibilità API** per **.net 4,6** o **.NET standard 2,0**</span><span class="sxs-lookup"><span data-stu-id="2605c-120">**Edit** > **Project Settings** > **Player** > **Configuration** > **Api Compatibility Level** to **.NET 4.6** or **.NET Standard 2.0**</span></span>
2) <span data-ttu-id="2605c-121">La direttiva per il preprocessore **ENABLE_WINMD_SUPPORT** deve essere racchiusa tra qualsiasi codice sfruttato in WinRT</span><span class="sxs-lookup"><span data-stu-id="2605c-121">The preprocessor directive **ENABLE_WINMD_SUPPORT** must be wrapped around any WinRT-leveraged code</span></span>

<span data-ttu-id="2605c-122">Il frammento di codice seguente si trova nella pagina manuale di Unity per [piattaforma UWP (Universal Windows Platform): API WinRT negli script C#](https://docs.unity3d.com/Manual/windowsstore-scripts.html).</span><span class="sxs-lookup"><span data-stu-id="2605c-122">The following code snippet is from the Unity manual page for [Universal Windows Platform: WinRT API in C# scripts](https://docs.unity3d.com/Manual/windowsstore-scripts.html).</span></span> <span data-ttu-id="2605c-123">In questo esempio viene restituito un ID pubblicitario, ma solo in UWP e Xbox One viene compilata:</span><span class="sxs-lookup"><span data-stu-id="2605c-123">In this example, an advertising ID is returned, but only on UWP and Xbox One builds:</span></span>

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

## <a name="edit-your-scripts-in-a-unity-c-project"></a><span data-ttu-id="2605c-124">Modificare gli script in un progetto C# Unity</span><span class="sxs-lookup"><span data-stu-id="2605c-124">Edit your scripts in a Unity C# project</span></span>

<span data-ttu-id="2605c-125">Quando si fa doppio clic su uno script nell'editor di Unity, viene avviato per impostazione predefinita lo script in un progetto di editor.</span><span class="sxs-lookup"><span data-stu-id="2605c-125">When you double-click a script in the Unity editor, it will by default launch your script in an editor project.</span></span> <span data-ttu-id="2605c-126">Le API di WinRT sembreranno sconosciute perché il progetto di Visual Studio non fa riferimento al Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="2605c-126">The WinRT APIs will appear to be unknown because the Visual Studio project doesn't reference the Windows Runtime.</span></span> <span data-ttu-id="2605c-127">La direttiva **ENABLE_WINMD_SUPPORT** non è definita e qualsiasi codice *#if* con wrapper viene ignorato finché il progetto non viene compilato in una soluzione UWP di Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2605c-127">The **ENABLE_WINMD_SUPPORT** directive is undefined and any *#if* wrapped code is ignored until you build your project into a UWP Visual Studio solution.</span></span>

## <a name="see-also"></a><span data-ttu-id="2605c-128">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2605c-128">See also</span></span>
* [<span data-ttu-id="2605c-129">Esportazione e creazione di una soluzione di Visual Studio Unity</span><span class="sxs-lookup"><span data-stu-id="2605c-129">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="2605c-130">Unity support Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="2605c-130">Windows Runtime Support Unity</span></span>](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)