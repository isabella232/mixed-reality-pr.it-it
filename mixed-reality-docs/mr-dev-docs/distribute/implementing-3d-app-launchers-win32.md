---
title: Implementare utilità di avvio per app 3D (app Win32)
description: Informazioni su come creare programmi di avvio e logo di app 3D per app e giochi Win32 VR per il menu Start e l'ambiente Home.
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, logo, icona, modellazione, avvio, utilità di avvio 3D, riquadro, cubo attivo, Win32, auricolare realtà mista, auricolare di realtà misto di Windows, auricolare della realtà virtuale, manifesto
ms.openlocfilehash: 46d3419d3c8267291496d8f788103d7002e6f230
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583036"
---
# <a name="implement-3d-app-launchers-win32-apps"></a><span data-ttu-id="bca54-104">Implementare utilità di avvio per app 3D (app Win32)</span><span class="sxs-lookup"><span data-stu-id="bca54-104">Implement 3D app launchers (Win32 apps)</span></span>

> [!NOTE]
> <span data-ttu-id="bca54-105">Questa funzionalità è disponibile solo per i PC che eseguono i più recenti voli di [Windows Insider](https://insider.windows.com) (RS5), Build 17704 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="bca54-105">This feature is only available to PCs running the latest [Windows Insider](https://insider.windows.com) flights (RS5), build 17704 and newer.</span></span>

<span data-ttu-id="bca54-106">La [Home realtà mista di Windows](../discover/navigating-the-windows-mixed-reality-home.md) è il punto di partenza in cui gli utenti atterrano prima di avviare le applicazioni.</span><span class="sxs-lookup"><span data-stu-id="bca54-106">The [Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="bca54-107">Per impostazione predefinita, è necessario avviare app e giochi in modalità VR di Win32 immersivi dall'esterno dell'auricolare e non verranno visualizzati nell'elenco "tutte le app" nel menu Start della realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="bca54-107">By default, you need to launch immersive Win32 VR apps and games from outside the headset and won't appear in the "All apps" list on the Windows Mixed Reality Start menu.</span></span> <span data-ttu-id="bca54-108">Se si seguono le istruzioni riportate in questo articolo per implementare un'utilità di avvio delle app 3D, è possibile avviare l'esperienza immersiva Win32 VR dal menu Start della realtà mista di Windows e dall'ambiente domestico.</span><span class="sxs-lookup"><span data-stu-id="bca54-108">If you follow the instructions in this article to implement a 3D app launcher, your immersive Win32 VR experience can be launched from within the Windows Mixed Reality Start menu and home environment.</span></span>

<span data-ttu-id="bca54-109">Questa operazione è valida solo per le esperienze di Win32 VR immersive distribuite al di fuori del vapore.</span><span class="sxs-lookup"><span data-stu-id="bca54-109">This is only true for immersive Win32 VR experiences distributed outside of Steam.</span></span> <span data-ttu-id="bca54-110">Per le esperienze VR [distribuite tramite Steam](../develop/porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md), è stata [aggiornata la realtà mista di Windows per SteamVR beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) insieme ai più recenti voli RS5 di Windows Insider, in modo che i titoli SteamVR siano visualizzati nel menu Start della realtà mista di Windows nell'elenco "tutte le app" utilizzando automaticamente un'utilità di avvio predefinita.</span><span class="sxs-lookup"><span data-stu-id="bca54-110">For VR experiences [distributed through Steam](../develop/porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md), we've [updated the Windows Mixed Reality for SteamVR Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) along with the latest Windows Insider RS5 flights so that SteamVR titles show up in the Windows Mixed Reality Start menu in the "All apps" list automatically using a default launcher.</span></span> <span data-ttu-id="bca54-111">In altre parole, il metodo descritto in questo articolo non è necessario per i titoli SteamVR e verrà sostituito dalla realtà mista di Windows per la funzionalità beta di SteamVR.</span><span class="sxs-lookup"><span data-stu-id="bca54-111">In other words, the method described in this article is unnecessary for SteamVR titles and will be overridden by the Windows Mixed Reality for SteamVR Beta functionality.</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="bca54-112">processo di creazione dell'utilità di avvio delle app 3D</span><span class="sxs-lookup"><span data-stu-id="bca54-112">3D app launcher creation process</span></span>

<span data-ttu-id="bca54-113">Per la creazione di un avvio di app 3D sono disponibili tre passaggi:</span><span class="sxs-lookup"><span data-stu-id="bca54-113">There are three steps to creating a 3D app launcher:</span></span>
1. [<span data-ttu-id="bca54-114">Progettazione e concezione</span><span class="sxs-lookup"><span data-stu-id="bca54-114">Designing and concepting</span></span>](3d-app-launcher-design-guidance.md)
2. [<span data-ttu-id="bca54-115">Modellazione ed esportazione</span><span class="sxs-lookup"><span data-stu-id="bca54-115">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="bca54-116">Integrazione nell'applicazione (questo articolo)</span><span class="sxs-lookup"><span data-stu-id="bca54-116">Integrating it into your application (this article)</span></span>

<span data-ttu-id="bca54-117">gli asset 3D da usare come avvii per l'applicazione devono essere creati usando le [linee guida per la creazione di realtà miste di Windows](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) per garantire la compatibilità.</span><span class="sxs-lookup"><span data-stu-id="bca54-117">3D assets to be used as launchers for your application should be authored using the [Windows Mixed Reality authoring guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) to ensure compatibility.</span></span> <span data-ttu-id="bca54-118">Non verrà eseguito il rendering degli asset che non soddisfano questa specifica di authoring nella Home page della realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="bca54-118">Assets that fail to meet this authoring specification won't be rendered in the Windows Mixed Reality home.</span></span>

## <a name="configuring-the-3d-launcher"></a><span data-ttu-id="bca54-119">Configurazione dell'utilità di avvio 3D</span><span class="sxs-lookup"><span data-stu-id="bca54-119">Configuring the 3D launcher</span></span>

<span data-ttu-id="bca54-120">Le applicazioni Win32 verranno visualizzate nell'elenco "tutte le app" nel menu di avvio della realtà mista di Windows se si crea un Launcher di app 3D.</span><span class="sxs-lookup"><span data-stu-id="bca54-120">Win32 applications will appear in the "All apps" list on the Windows Mixed Reality Start menu if you create a 3D app launcher for them.</span></span> <span data-ttu-id="bca54-121">A tale scopo, creare un file XML del [manifesto degli elementi visivi](/previous-versions/windows/apps/dn393983(v=win.10)) che fa riferimento all'utilità di avvio delle app 3D attenendosi alla procedura seguente:</span><span class="sxs-lookup"><span data-stu-id="bca54-121">To do that, create a [Visual Elements Manifest](/previous-versions/windows/apps/dn393983(v=win.10)) XML file referencing the 3D App Launcher by following these steps:</span></span>

1. <span data-ttu-id="bca54-122">Creare un **file GLB asset di avvio app 3D** (vedere [modellazione ed esportazione](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)).</span><span class="sxs-lookup"><span data-stu-id="bca54-122">Create a **3D App Launcher asset GLB file** (See [Modeling and exporting](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)).</span></span>
2. <span data-ttu-id="bca54-123">Creare un **[manifesto degli elementi visivi](/previous-versions/windows/apps/dn393983(v=win.10))** per l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="bca54-123">Create a **[Visual Elements Manifest](/previous-versions/windows/apps/dn393983(v=win.10))** for your application.</span></span>
    1. <span data-ttu-id="bca54-124">È possibile iniziare con l' [esempio riportato di seguito](#sample-visual-elements-manifest).</span><span class="sxs-lookup"><span data-stu-id="bca54-124">You can start with the [sample below](#sample-visual-elements-manifest).</span></span>  <span data-ttu-id="bca54-125">Per altri dettagli, vedere la documentazione completa del [manifesto degli elementi visivi](/previous-versions/windows/apps/dn393983(v=win.10)) .</span><span class="sxs-lookup"><span data-stu-id="bca54-125">See the full [Visual Elements Manifest](/previous-versions/windows/apps/dn393983(v=win.10)) documentation for more details.</span></span>
    2. <span data-ttu-id="bca54-126">Aggiornare **Square150x150Logo** e **SQUARE70X70LOGO** con un png/jpg/gif per l'app.</span><span class="sxs-lookup"><span data-stu-id="bca54-126">Update **Square150x150Logo** and **Square70x70Logo** with a PNG/JPG/GIF for your app.</span></span>
        * <span data-ttu-id="bca54-127">Questi verranno usati per il logo 2D dell'app nell'elenco di tutte le app della realtà mista di Windows e per il menu Start sul desktop.</span><span class="sxs-lookup"><span data-stu-id="bca54-127">These will be used for the app’s 2D logo in the Windows Mixed Reality All Apps list and for the Start Menu on desktop.</span></span>
        * <span data-ttu-id="bca54-128">Il percorso del file è basato sulla cartella che contiene il manifesto degli elementi visivi.</span><span class="sxs-lookup"><span data-stu-id="bca54-128">The file path is based on the folder containing the Visual Elements Manifest.</span></span>
        * <span data-ttu-id="bca54-129">È comunque necessario fornire un'icona del menu Start Desktop per l'app attraverso i meccanismi standard.</span><span class="sxs-lookup"><span data-stu-id="bca54-129">You still need to provide a desktop Start Menu icon for your app through the standard mechanisms.</span></span> <span data-ttu-id="bca54-130">Questo può essere direttamente nell'eseguibile o nel collegamento creato.</span><span class="sxs-lookup"><span data-stu-id="bca54-130">This can either be directly in the executable or in the shortcut you create.</span></span> <span data-ttu-id="bca54-131">Ad esempio, tramite IShellLink:: SetIconLocation.</span><span class="sxs-lookup"><span data-stu-id="bca54-131">For example, via IShellLink::SetIconLocation.</span></span>
        * <span data-ttu-id="bca54-132">*Facoltativo:* È possibile usare un file resources. pri se si vuole che MRT fornisca più dimensioni di asset per diverse scale di risoluzione e temi a contrasto elevato.</span><span class="sxs-lookup"><span data-stu-id="bca54-132">*Optional:* You can use a resources.pri file if you would like for MRT to provide multiple asset sizes for different resolution scales and high contrast themes.</span></span>
    3. <span data-ttu-id="bca54-133">Aggiornare il **percorso di MixedRealityModel** in modo che punti al GLB per l'utilità di avvio dell'app 3D</span><span class="sxs-lookup"><span data-stu-id="bca54-133">Update the **MixedRealityModel Path** to point to the GLB for your 3D App Launcher</span></span>
    4. <span data-ttu-id="bca54-134">Salvare il file con lo stesso nome del file eseguibile, con estensione ".VisualElementsManifest.xml" e salvarlo nella stessa directory.</span><span class="sxs-lookup"><span data-stu-id="bca54-134">Save the file with the same name as your executable file, with an extension of ".VisualElementsManifest.xml" and save it in the same directory.</span></span> <span data-ttu-id="bca54-135">Per il file eseguibile "contoso.exe", ad esempio, il file XML associato è denominato "contoso.visualelementsmanifest.xml".</span><span class="sxs-lookup"><span data-stu-id="bca54-135">For example, for the executable file "contoso.exe", the accompanying XML file is named "contoso.visualelementsmanifest.xml".</span></span>
3. <span data-ttu-id="bca54-136">**Aggiungere un collegamento** all'applicazione nel menu Start di Windows desktop.</span><span class="sxs-lookup"><span data-stu-id="bca54-136">**Add a shortcut** to your application to the desktop Windows Start Menu.</span></span> <span data-ttu-id="bca54-137">Per un'implementazione C++ di esempio, vedere l' [esempio seguente](#sample-app-launcher-shortcut-creation) .</span><span class="sxs-lookup"><span data-stu-id="bca54-137">See the [sample below](#sample-app-launcher-shortcut-creation) for an example C++ implementation.</span></span> 
    * <span data-ttu-id="bca54-138">Crearlo in%ALLUSERSPROFILE%\Microsoft\Windows\Start Avvio\programmi (Machine) o%APPDATA%\Microsoft\Windows\Start Avvio\programmi (User)</span><span class="sxs-lookup"><span data-stu-id="bca54-138">Create it in %ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs (machine) or %APPDATA%\Microsoft\Windows\Start Menu\Programs (user)</span></span>
    * <span data-ttu-id="bca54-139">Se un aggiornamento modifica il manifesto degli elementi visivi o gli asset a cui fa riferimento, il programma di aggiornamento o il programma di installazione dovrebbe aggiornare il collegamento in modo che il manifesto venga analizzato e aggiornato gli asset memorizzati nella cache.</span><span class="sxs-lookup"><span data-stu-id="bca54-139">If an update changes your visual elements manifest or the assets referenced by it, the updater or installer should update the shortcut such that the manifest is reparsed and cached assets are updated.</span></span>
4. <span data-ttu-id="bca54-140">*Facoltativo:* Se il collegamento sul desktop non punta direttamente al file EXE dell'applicazione (ad esempio, se richiama un gestore di protocollo personalizzato come "myapp://"), il menu Start non troverà automaticamente il file di VisualElementsManifest.xml dell'app.</span><span class="sxs-lookup"><span data-stu-id="bca54-140">*Optional:* If your desktop shortcut doesn't point directly to your application’s EXE (for example, if it invokes a custom protocol handler like “myapp://”), the Start Menu won’t automatically find the app’s VisualElementsManifest.xml file.</span></span> <span data-ttu-id="bca54-141">Per risolvere il problema, è necessario che il collegamento specifichi il percorso del file del manifesto degli elementi visivi utilizzando System. AppUserModel. VisualElementsManifestHintPath ().</span><span class="sxs-lookup"><span data-stu-id="bca54-141">To resolve this, the shortcut should specify the file path of the Visual Elements Manifest using System.AppUserModel.VisualElementsManifestHintPath ().</span></span> <span data-ttu-id="bca54-142">Questa impostazione può essere configurata nel collegamento utilizzando le stesse tecniche di System.AppUserModel.ID.</span><span class="sxs-lookup"><span data-stu-id="bca54-142">This can be set in the shortcut using the same techniques as System.AppUserModel.ID.</span></span> <span data-ttu-id="bca54-143">Non è necessario utilizzare System.AppUserModel.ID, ma è possibile eseguire questa operazione se si desidera che il collegamento corrisponda all'ID del modello utente dell'applicazione esplicita se ne viene utilizzato uno.</span><span class="sxs-lookup"><span data-stu-id="bca54-143">You aren't required to use System.AppUserModel.ID but you may do so if you wish for the shortcut to match the explicit Application User Model ID of the application if one is used.</span></span>  <span data-ttu-id="bca54-144">Per un esempio C++, vedere la sezione relativa alla [creazione del collegamento dell'utilità di avvio delle app di esempio](#sample-app-launcher-shortcut-creation) .</span><span class="sxs-lookup"><span data-stu-id="bca54-144">See the [sample app launcher shortcut creation](#sample-app-launcher-shortcut-creation) section below for a C++ sample.</span></span>

### <a name="sample-visual-elements-manifest"></a><span data-ttu-id="bca54-145">Manifesto degli elementi visivi di esempio</span><span class="sxs-lookup"><span data-stu-id="bca54-145">Sample Visual Elements Manifest</span></span>

```xml
<Application xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance">
  <VisualElements
    ShowNameOnSquare150x150Logo="on"
    Square150x150Logo="YOUR_APP_LOGO_150X150.png"
    Square70x70Logo=" YOUR_APP_LOGO_70X70.png"
    ForegroundText="light"
    BackgroundColor="#000000">
    <MixedRealityModel Path="YOUR_3D_APP_LAUNCHER_ASSET.glb">
        <SpatialBoundingBox Center="0,0,0" Extents="Auto" />
    </MixedRealityModel>
  </VisualElements>
</Application>
```

### <a name="sample-app-launcher-shortcut-creation"></a><span data-ttu-id="bca54-146">Creazione di un collegamento dell'utilità di avvio app di esempio</span><span class="sxs-lookup"><span data-stu-id="bca54-146">Sample app launcher shortcut creation</span></span>

<span data-ttu-id="bca54-147">Il codice di esempio seguente illustra come creare un collegamento in C++, incluso l'override del percorso del file XML del manifesto degli elementi visivi.</span><span class="sxs-lookup"><span data-stu-id="bca54-147">The sample code below shows how you can create a shortcut in C++, including overriding the path to the Visual Elements Manifest XML file.</span></span> <span data-ttu-id="bca54-148">Si noti che l'override è necessario solo nei casi in cui il collegamento non punti direttamente al file EXE associato al manifesto (ad esempio, il collegamento usa un gestore di protocollo personalizzato come "myapp://").</span><span class="sxs-lookup"><span data-stu-id="bca54-148">Note the override is only required in cases where your shortcut doesn't point directly to the EXE associated with the manifest (for example, your shortcut uses a custom protocol handler like "myapp://").</span></span>

#### <a name="sample-lnk-shortcut-creation-c"></a><span data-ttu-id="bca54-149">Esempio. Creazione di collegamenti LNK (C++)</span><span class="sxs-lookup"><span data-stu-id="bca54-149">Sample .LNK shortcut creation (C++)</span></span>

```cpp
#include <windows.h>
#include <propkey.h>
#include <shlobj_core.h>
#include <shlwapi.h>
#include <propvarutil.h>
#include <wrl.h>

#include <memory>

using namespace Microsoft::WRL;

#define RETURN_IF_FAILED(x) do { HRESULT hr = x; if (FAILED(hr)) { return hr; } } while(0)
#define RETURN_IF_WIN32_BOOL_FALSE(x) do { DWORD res = x; if (res == 0) { return HRESULT_FROM_WIN32(GetLastError()); } } while(0)

int wmain()
{
    RETURN_IF_FAILED(CoInitializeEx(nullptr, COINIT_APARTMENTTHREADED));

    ComPtr<IShellLink> shellLink;
    RETURN_IF_FAILED(CoCreateInstance(__uuidof(ShellLink), nullptr, CLSCTX_INPROC_SERVER, IID_PPV_ARGS(&shellLink)));
    RETURN_IF_FAILED(shellLink->SetPath(L"MyLauncher://launch/app-identifier"));

    // It is also possible to use an icon file in another location. For example, "C:\Program Files (x86)\MyLauncher\assets\app-identifier.ico".
    RETURN_IF_FAILED(shellLink->SetIconLocation(L"C:\\Program Files (x86)\\MyLauncher\\apps\\app-identifier\\game.exe", 0 /*iIcon*/));

    ComPtr<IPropertyStore> propStore;
    RETURN_IF_FAILED(shellLink.As(&propStore));

    {
        // Optional: If the application has an explict Application User Model ID, then you should usually specify it in the shortcut.
        PROPVARIANT propVar;
        RETURN_IF_FAILED(InitPropVariantFromString(L"ExplicitAppUserModelID", &propVar));
        RETURN_IF_FAILED(propStore->SetValue(PKEY_AppUserModel_ID, propVar));
        PropVariantClear(&propVar);
    }

    {
        // A hint path to the manifest is only necessary if the target path of the shortcut is not a file path to the executable.
        // By convention the manifest is named <executable name>.VisualElementsManifest.xml and is in the same folder as the executable
        // (and resources.pri if applicable). Assets referenced by the manifest are relative to the folder containing the manifest.

        //
        // PropKey.h
        //
        //  Name:     System.AppUserModel.VisualElementsManifestHintPath -- PKEY_AppUserModel_VisualElementsManifestHintPath
        //  Type:     String -- VT_LPWSTR  (For variants: VT_BSTR)
        //  FormatID: {9F4C2855-9F79-4B39-A8D0-E1D42DE1D5F3}, 31
        //  
        //  Suggests where to look for the VisualElementsManifest for a Win32 app
        //
        // DEFINE_PROPERTYKEY(PKEY_AppUserModel_VisualElementsManifestHintPath, 0x9F4C2855, 0x9F79, 0x4B39, 0xA8, 0xD0, 0xE1, 0xD4, 0x2D, 0xE1, 0xD5, 0xF3, 31);
        // #define INIT_PKEY_AppUserModel_VisualElementsManifestHintPath { { 0x9F4C2855, 0x9F79, 0x4B39, 0xA8, 0xD0, 0xE1, 0xD4, 0x2D, 0xE1, 0xD5, 0xF3 }, 31 }

        PROPVARIANT propVar;
        RETURN_IF_FAILED(InitPropVariantFromString(L"C:\\Program Files (x86)\\MyLauncher\\apps\\app-identifier\\game.visualelementsmanifest.xml", &propVar));
        RETURN_IF_FAILED(propStore->SetValue(PKEY_AppUserModel_VisualElementsManifestHintPath, propVar));
        PropVariantClear(&propVar);
    }

    constexpr PCWSTR shortcutPath = L"%APPDATA%\\Microsoft\\Windows\\Start Menu\\Programs\\game.lnk";
    const DWORD requiredBufferLength = ExpandEnvironmentStrings(shortcutPath, nullptr, 0);
    RETURN_IF_WIN32_BOOL_FALSE(requiredBufferLength);

    const auto expandedShortcutPath = std::make_unique<wchar_t[]>(requiredBufferLength);
    RETURN_IF_WIN32_BOOL_FALSE(ExpandEnvironmentStrings(shortcutPath, expandedShortcutPath.get(), requiredBufferLength));

    ComPtr<IPersistFile> persistFile;
    RETURN_IF_FAILED(shellLink.As(&persistFile));
    RETURN_IF_FAILED(persistFile->Save(expandedShortcutPath.get(), FALSE));

    return 0;
}
```

#### <a name="sample-url-launcher-shortcut"></a><span data-ttu-id="bca54-150">Esempio. Collegamento all'utilità di avvio URL</span><span class="sxs-lookup"><span data-stu-id="bca54-150">Sample .URL launcher shortcut</span></span> 

```
[{9F4C2855-9F79-4B39-A8D0-E1D42DE1D5F3}]
Prop31=C:\Program Files (x86)\MyLauncher\apps\app-identifier\game.visualelementsmanifest.xml
Prop5=ExplicitAppUserModelID

[{000214A0-0000-0000-C000-000000000046}]
Prop3=19,0

[InternetShortcut]
IDList=
URL=MyLauncher://launch/app-identifier
IconFile=C:\Program Files (x86)\MyLauncher\apps\app-identifier\game.exe
IconIndex=0
```

## <a name="see-also"></a><span data-ttu-id="bca54-151">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="bca54-151">See also</span></span>

* <span data-ttu-id="bca54-152">[Esempio di modello di realtà mista](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) contenente un utilità di avvio delle app 3D.</span><span class="sxs-lookup"><span data-stu-id="bca54-152">[Mixed reality model sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) containing a 3D app launcher.</span></span>
* [<span data-ttu-id="bca54-153">Linee guida per la progettazione di utilità di avvio di app 3D</span><span class="sxs-lookup"><span data-stu-id="bca54-153">3D app launcher design guidance</span></span>](3d-app-launcher-design-guidance.md)
* [<span data-ttu-id="bca54-154">Creazione di modelli 3D per l'utilizzo nella Home realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="bca54-154">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="bca54-155">Implementazione di lanci di app 3D (app UWP)</span><span class="sxs-lookup"><span data-stu-id="bca54-155">Implementing 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="bca54-156">Esplorazione dello spazio iniziale di Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="bca54-156">Navigating the Windows Mixed Reality home</span></span>](../discover/navigating-the-windows-mixed-reality-home.md)