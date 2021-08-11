---
title: Implementare utilità di avvio per app 3D (app Win32)
description: Informazioni su come creare utilità di avvio e logo di app 3D per app e giochi win32 VR per l'ambiente menu Start e home.
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, logo, icona, modellazione, launcher, utilità di avvio 3D, riquadro, cubo live, win32, visore VR di realtà mista, visore VR windows mixed reality, visore VR di realtà virtuale, manifesto
ms.openlocfilehash: 60eb4f543f287e833033c8e1852e2a85c6040d3c76455aadaca4b37c0a632573
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198767"
---
# <a name="implement-3d-app-launchers-win32-apps"></a>Implementare utilità di avvio per app 3D (app Win32)

> [!NOTE]
> Questa funzionalità è disponibile solo per i PC che eseguono i più [recenti Windows Insider](https://insider.windows.com) (RS5), build 17704 e versioni più recenti.

La [Windows Mixed Reality iniziale è il](../discover/navigating-the-windows-mixed-reality-home.md) punto di partenza da cui gli utenti atterrerà prima di avviare le applicazioni. Per impostazione predefinita, devi avviare app e giochi vr Win32 immersive dall'esterno del visore VR e non verrà visualizzato nell'elenco "Tutte le app" nel Windows Mixed Reality menu Start. Se si seguono le istruzioni in questo articolo per implementare un'utilità di avvio di app 3D, l'esperienza di realtà virtuale Win32 immersiva può essere avviata dall'interno dell'ambiente Windows Mixed Reality menu Start e home.

Questo vale solo per le esperienze immersive di realtà virtuale Win32 distribuite all'esterno di Steam. Per le esperienze di realtà virtuale distribuite tramite [Steam,](../develop/porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)è stato aggiornato il Windows Mixed Reality per La versione [beta di SteamVR](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) insieme alle versioni più recenti dei voli di Windows Insider RS5 in modo che i titoli di LauncherVR appaiano automaticamente nel Windows Mixed Reality menu Start nell'elenco "Tutte le app" usando un'utilità di avvio predefinita. In altre parole, il metodo descritto in questo articolo non è necessario per i titoli di SteamVR e verrà sostituito dalla Windows Mixed Reality per La versione beta di SteamVR.

## <a name="3d-app-launcher-creation-process"></a>Processo di creazione dell'utilità di avvio delle app 3D

Per creare un'utilità di avvio di app 3D, è necessario eseguire tre passaggi:
1. [Progettazione e creazione di concetti](3d-app-launcher-design-guidance.md)
2. [Modellazione ed esportazione](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. Integrazione nell'applicazione (questo articolo)

Gli asset 3D da usare come utilità di avvio per l'applicazione devono essere creati usando le linee guida Windows Mixed Reality [creazione](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) di applicazioni per garantire la compatibilità. Gli asset che non soddisfano questa specifica di creazione non verranno sottoposti a rendering nella Windows Mixed Reality home.

## <a name="configuring-the-3d-launcher"></a>Configurazione dell'utilità di avvio 3D

Le applicazioni Win32 verranno visualizzate nell'elenco "Tutte le app" Windows Mixed Reality menu Start se si crea un'utilità di avvio di app 3D. A tale scopo, creare un file XML del manifesto degli [elementi](/previous-versions/windows/apps/dn393983(v=win.10)) visivi che fa riferimento all'utilità di avvio delle app 3D seguendo questa procedura:

1. Creare un **file GLB di asset dell'utilità** di avvio delle app 3D (vedere [Modellazione ed esportazione).](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
2. Creare un **[manifesto degli elementi visivi](/previous-versions/windows/apps/dn393983(v=win.10))** per l'applicazione.
    1. È possibile iniziare con [l'esempio seguente.](#sample-visual-elements-manifest)  Per altri [dettagli, vedere](/previous-versions/windows/apps/dn393983(v=win.10)) la documentazione completa sul manifesto degli elementi visivi.
    2. Aggiornare **Square150x150Logo** e **Square70x70Logo** con un file PNG/JPG/GIF per l'app.
        * Questi verranno usati per il logo 2D dell'app nell'elenco Windows Mixed Reality Tutte le app e per il menu Start sul desktop.
        * Il percorso del file è basato sulla cartella contenente il manifesto degli elementi visivi.
        * È comunque necessario fornire un'icona del menu Start sul desktop per l'app tramite i meccanismi standard. Può essere direttamente nel file eseguibile o nel collegamento creato. Ad esempio, tramite IShellLink::SetIconLocation.
        * *Facoltativo:* È possibile usare un file resources.pri se si vuole che MRT fornisse più dimensioni di asset per diverse scale di risoluzione e temi a contrasto elevato.
    3. Aggiornare il **percorso MixedRealityModel** in modo che punti al GLB per l'utilità di avvio delle app 3D
    4. Salvare il file con lo stesso nome del file eseguibile, con estensione ".VisualElementsManifest.xml" e salvarlo nella stessa directory. Ad esempio, per il file eseguibile "contoso.exe", il file XML di accompagnamento è denominato "contoso.visualelementsmanifest.xml".
3. **Aggiungere un collegamento** all'applicazione sul desktop Windows Menu Start. Vedere [l'esempio seguente per](#sample-app-launcher-shortcut-creation) un'implementazione C++ di esempio. 
    * Crearlo in %ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs (computer) o %APPDATA%\Microsoft\Windows\Start Menu\Programs (utente)
    * Se un aggiornamento modifica il manifesto degli elementi visivi o gli asset a cui fa riferimento, lo strumento di aggiornamento o il programma di installazione deve aggiornare il collegamento in modo che il manifesto sia analizzato di nuovo e che gli asset memorizzati nella cache siano aggiornati.
4. *Facoltativo:* Se il collegamento sul desktop non punta direttamente al file EXE dell'applicazione (ad esempio, se richiama un gestore di protocollo personalizzato come "myapp://"), il menu Start non troverà automaticamente il file VisualElementsManifest.xml dell'app. Per risolvere il problema, il collegamento deve specificare il percorso del file del manifesto degli elementi visivi usando System.AppUserModel.VisualElementsManifestHintPath (). Questa impostazione può essere impostata nel collegamento usando le stesse tecniche di System.AppUserModel.ID. Non è necessario usare System.AppUserModel.ID, ma è possibile farlo se si vuole che il collegamento corrisponda all'ID modello utente applicazione esplicito dell'applicazione, se ne viene usato uno.  Per un esempio [di C++,](#sample-app-launcher-shortcut-creation) vedere la sezione creazione di un collegamento dell'utilità di avvio delle app di esempio riportata di seguito.

### <a name="sample-visual-elements-manifest"></a>Manifesto degli elementi visivi di esempio

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

### <a name="sample-app-launcher-shortcut-creation"></a>Creazione di un esempio di collegamento dell'utilità di avvio delle app

Il codice di esempio seguente illustra come creare un collegamento in C++, inclusa l'override del percorso del file XML del manifesto degli elementi visivi. Si noti che l'override è necessario solo nei casi in cui il collegamento non punta direttamente al file EXE associato al manifesto (ad esempio, il collegamento usa un gestore di protocollo personalizzato come "myapp://").

#### <a name="sample-lnk-shortcut-creation-c"></a>Esempio. Creazione di un collegamento LNK (C++)

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

#### <a name="sample-url-launcher-shortcut"></a>Esempio. Collegamento dell'utilità di avvio URL 

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

## <a name="see-also"></a>Vedi anche

* [Esempio di modello di realtà mista](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) contenente un'utilità di avvio di app 3D.
* [Linee guida per la progettazione di utilità di avvio di app 3D](3d-app-launcher-design-guidance.md)
* [Creazione di modelli 3D da usare nella home Windows Mixed Reality home](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Implementazione di utilità di avvio di app 3D (app UWP)](implementing-3d-app-launchers.md)
* [Esplorazione dello spazio iniziale di Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md)