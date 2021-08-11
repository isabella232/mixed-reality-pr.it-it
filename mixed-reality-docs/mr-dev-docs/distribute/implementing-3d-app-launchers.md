---
title: Implementare utilità di avvio per app 3D (app UWP)
description: Informazioni su come creare utilità di avvio di app e logo 3D per Windows Mixed Reality app e giochi UWP in HoloLens visori VR.
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, logo, icona, modellazione, launcher, utilità di avvio 3D, riquadro, cubo live, collegamento diretto, secondarytile, riquadro secondario, UWP, visore VR realtà mista, visore VR windows mixed reality, visore VR di realtà virtuale, XML, rettangolo di selezione, unity
ms.openlocfilehash: b0ccff2aaba9c4693f58b134cdb3af9190b59befec0b31851273ed6a3bc1fc04
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196422"
---
# <a name="implement-3d-app-launchers-uwp-apps"></a>Implementare utilità di avvio per app 3D (app UWP)

> [!NOTE]
> Questa funzionalità è stata aggiunta come parte di Fall Creators Update (RS3) 2017 per visori VR immersive ed è supportata da HoloLens con l'aggiornamento di Windows 10 aprile 2018. Assicurarsi che la destinazione dell'applicazione sia una versione di Windows SDK maggiore o uguale a 10.0.16299 nei visori VR immersive e 10.0.17125 in HoloLens. La versione più recente di Windows SDK [è disponibile qui.](https://developer.microsoft.com/windows/downloads/windows-10-sdk)

La [Windows Mixed Reality iniziale è il](../discover/navigating-the-windows-mixed-reality-home.md) punto di partenza da cui gli utenti atterrerà prima di avviare le applicazioni. Quando si crea un'applicazione UWP per Windows Mixed Reality, per impostazione predefinita, le app vengono avviate come slate 2D con il logo dell'app. Quando si sviluppano esperienze per Windows Mixed Reality, è possibile definire facoltativamente un'utilità di avvio 3D per eseguire l'override dell'utilità di avvio 2D predefinita per l'applicazione. In generale, le utilità di avvio 3D sono consigliate per l'avvio di applicazioni immersive che consentono agli utenti di uscire Windows Mixed Reality home. L'utilità di avvio 2D predefinita è preferibile quando l'app viene attivata sul posto. Puoi anche creare un collegamento [diretto 3D (secondaryTile)](#3d-deep-links-secondarytiles) come utilità di avvio 3D al contenuto all'interno di un'app UWP 2D.

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a>Processo di creazione dell'utilità di avvio delle app 3D

Per creare un'utilità di avvio di app 3D, è necessario eseguire tre passaggi:
1. [Progettazione e creazione di concetti](3d-app-launcher-design-guidance.md)
2. [Modellazione ed esportazione](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. Integrazione nell'applicazione (questo articolo)

Gli asset 3D da usare come utilità di avvio per l'applicazione devono essere creati usando le linee guida per la creazione Windows Mixed Reality per [garantire](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) la compatibilità. Non verrà eseguito il rendering degli asset che non soddisfano questa specifica di creazione Windows Mixed Reality home.

## <a name="configuring-the-3d-launcher"></a>Configurazione dell'utilità di avvio 3D

Quando crei un nuovo progetto in Visual Studio, viene creato un riquadro predefinito semplice che visualizza il nome e il logo dell'app. Per sostituire questa rappresentazione 2D con un modello 3D personalizzato, modificare il manifesto dell'app dell'applicazione in modo da includere l'elemento "MixedRealityModel" come parte della definizione di riquadro predefinita. Per ripristinare l'utilità di avvio 2D, è sufficiente rimuovere la definizione MixedRealityModel dal manifesto.

### <a name="xml"></a>XML

Individuare prima di tutto il manifesto del pacchetto dell'app nel progetto corrente. Per impostazione predefinita, il manifesto sarà denominato Package.appxmanifest. Se si usa il Visual Studio, fare clic con il pulsante destro  del mouse sul manifesto nel visualizzatore di soluzioni e scegliere Visualizza origine per aprire il file XML per la modifica. 

All'inizio del manifesto aggiungere lo schema uap5 e includerlo come spazio dei nomi ignorabile:

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

Specificare quindi "MixedRealityModel" nel riquadro predefinito per l'applicazione:

```xml
<Applications>
    <Application Id="App"
      Executable="$targetnametoken$.exe"
      EntryPoint="ExampleApp.App">
      <uap:VisualElements
        DisplayName="ExampleApp"
        Square150x150Logo="Assets\Logo.png"
        Square44x44Logo="Assets\SmallLogo.png"
        Description="ExampleApp"
        BackgroundColor="#464646">
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb" />
        </uap:DefaultTile>
        <uap:SplashScreen Image="Assets\SplashScreen.png" />
      </uap:VisualElements>
    </Application>
</Applications>
```

L'elemento MixedRealityModel accetta un percorso di file che punta a un asset 3D archiviato nel pacchetto dell'app. Attualmente sono supportati solo i modelli 3D recapitati usando il formato di file con estensione glb e creati in base alle istruzioni Windows Mixed Reality creazione di [asset 3D.](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) Gli asset devono essere archiviati nel pacchetto dell'app e l'animazione non è attualmente supportata. Se il parametro "Path" viene lasciato vuoto, Windows lo slate 2D anziché l'utilità di avvio 3D. **Nota:** l'asset .glb deve essere contrassegnato come "Content" nelle impostazioni di compilazione prima di compilare ed eseguire l'app.


![Selezionare il file con estensione glb in Esplora soluzioni e usare la sezione properties per contrassegnarla come "Content" nelle impostazioni di compilazione](images/buildsetting-content-300px.png)<br>
*Selezionare il file con estensione glb in Esplora soluzioni e usare la sezione properties per contrassegnarla come "Content" nelle impostazioni di compilazione*

### <a name="bounding-box"></a>Rettangolo di selezione

Un rettangolo di selezione può essere usato per aggiungere facoltativamente un'area del buffer aggiuntiva intorno all'oggetto. Il rettangolo di selezione viene specificato usando un punto centrale e gli extent, che indicano la distanza dal centro del rettangolo di selezione ai relativi bordi lungo ogni asse. Le unità per il rettangolo di selezione possono essere mappate a 1 unità = 1 contatore. Se non viene specificato un rettangolo di selezione, ne verrà adattato automaticamente uno alla mesh dell'oggetto. Se il rettangolo di selezione specificato è più piccolo del modello, verrà ridimensionato per adattarsi alla mesh.

Il supporto per l'attributo del rettangolo di selezione verrà Windows'aggiornamento RS4 come proprietà nell'elemento MixedRealityModel. Per definire prima un rettangolo di selezione nella parte superiore del manifesto dell'app, aggiungere lo schema uap6 e includerlo come spazi dei nomi ignorabili:

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="http://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
Successivamente, in MixedRealityModel impostare la proprietà SpatialBoundingBox per definire il rettangolo di selezione: 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a>Uso di Unity

Quando si lavora con Unity, il progetto deve essere compilato e aperto in Visual Studio prima di poter modificare il manifesto dell'app. 

>[!NOTE]
>L'utilità di avvio 3D deve essere ridefinito nel manifesto durante la compilazione e la distribuzione di una nuova Visual Studio da Unity.

## <a name="3d-deep-links-secondarytiles"></a>Collegamenti diretti 3D (secondaryTiles)

> [!NOTE]
> Questa funzionalità è stata aggiunta come parte di Fall Creators Update (RS3) 2017 per visori VR immersive e come parte dell'aggiornamento di aprile 2018 (RS4) per HoloLens. Assicurarsi che la destinazione dell'applicazione sia una versione di Windows SDK maggiore o uguale a 10.0.16299 su visori VR immersive e 10.0.17125 in HoloLens. La versione più recente di Windows SDK [è disponibile qui.](https://developer.microsoft.com/windows/downloads/windows-10-sdk)

>[!IMPORTANT]
>I collegamenti diretti 3D (secondaryTiles) funzionano solo con le app UWP 2D. È tuttavia possibile creare un'utilità di avvio di [app 3D](implementing-3d-app-launchers.md) per avviare un'app esclusiva dalla home Windows Mixed Reality home.

Le applicazioni [2D](../discover/navigating-the-windows-mixed-reality-home.md) possono essere migliorate per il Windows Mixed Reality aggiungendo la possibilità di inserire modelli 3D dall'app nella home page di Windows Mixed Reality come collegamenti diretti al contenuto all'interno dell'app 2D, proprio come i riquadri secondari [2D](/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) nel Windows menu Start. Ad esempio, è possibile creare fotosfere a 360° che si collegano direttamente a un'app di visualizzazione foto a 360° o consentire agli utenti di inserire contenuto 3D da una raccolta di asset che apre una pagina dei dettagli sull'autore. Questi sono solo un paio di modi per espandere le funzionalità dell'applicazione 2D con contenuto 3D.

### <a name="creating-a-3d-secondarytile"></a>Creazione di un "secondaryTile" 3D

Puoi inserire contenuto 3D dall'applicazione usando "secondaryTiles" definendo un modello di realtà mista al momento della creazione. I modelli di realtà mista vengono creati facendo riferimento a un asset 3D nel pacchetto dell'app e, facoltativamente, definendo un rettangolo di selezione. 

> [!NOTE]
> La creazione di "secondaryTiles" dall'interno di una visualizzazione esclusiva non è attualmente supportata.

```cs
using Windows.UI.StartScreen;
using Windows.Foundation.Numerics;
using Windows.Perception.Spatial;

// Initialize the tile
SecondaryTile tile = new SecondaryTile("myTileId")
{
    DisplayName = "My Tile",
    Arguments = "myArgs"
};

tile.VisualElements.Square150x150Logo = new Uri("ms-appx:///Assets/MyTile/Square150x150Logo.png");

//Assign 3D model (only ms-appx and ms-appdata are allowed)
TileMixedRealityModel model = tile.VisualElements.MixedRealityModel;
model.Uri = new Uri("ms-appx:///Assets/MyTile/MixedRealityModel.glb");
model.ActivationBehavior = TileMixedRealityModelActivationBehavior.Default;
model.BoundingBox = new SpatialBoundingBox
{
    Center = new Vector3 { X = 1, Y = 0, Z = 0 },
    Extents = new Vector3 { X = 3, Y = 5, Z = 4 }
};

// And place it
await tile.RequestCreateAsync();
```

### <a name="bounding-box"></a>Rettangolo di selezione

Un rettangolo di selezione può essere usato per aggiungere un'area del buffer aggiuntiva intorno all'oggetto. Il rettangolo di selezione viene specificato usando un punto centrale e gli extent, che indicano la distanza dal centro del rettangolo di selezione ai relativi bordi lungo ogni asse. Le unità per il rettangolo di selezione possono essere mappate a 1 unità = 1 contatore. Se non viene specificato un rettangolo di selezione, ne verrà adattato automaticamente uno alla mesh dell'oggetto. Se il rettangolo di selezione specificato è più piccolo del modello, verrà ridimensionato per adattarsi alla mesh.

### <a name="activation-behavior"></a>Comportamento di attivazione

> [!NOTE]
> Questa funzionalità sarà supportata a Windows aggiornamento RS4. Se si prevede di usare questa funzionalità, assicurarsi che l'applicazione sia una versione di Windows SDK maggiore o uguale a 10.0.17125

Puoi definire il comportamento di attivazione per un secondaryTile 3D per controllare come reagisce quando un utente lo seleziona. Può essere usato per inserire oggetti 3D nella home page di Realtà mista puramente informativi o decorativi. Sono supportati i tipi di comportamento di attivazione seguenti:
1. Impostazione predefinita: quando un utente seleziona secondaryTile 3D, l'app viene attivata
2. Nessuno: quando l'utente seleziona il secondaryTile 3D, non accade nulla e l'app non viene attivata.

### <a name="obtaining-and-updating-an-existing-secondarytile"></a>Recupero e aggiornamento di un oggetto "secondaryTile" esistente

Gli sviluppatori possono ottenere un elenco dei riquadri secondari esistenti, che include le proprietà specificate in precedenza. Possono anche aggiornare le proprietà modificando il valore e quindi chiamando UpdateAsync().

```cs
// Grab the existing secondary tile
SecondaryTile tile = (await SecondaryTile.FindAllAsync()).First();

Uri updatedUri = new Uri("ms-appdata:///local/MixedRealityUpdated.glb");

// See if the model needs updating
if (!tile.VisualElements.MixedRealityModel.Uri.Equals(updatedUri))
{
    // Update it
    tile.VisualElements.MixedRealityModel.Uri = updatedUri;

    // And apply the changes
    await tile.UpdateAsync();
}
```

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a>Verifica che l'utente sia in Windows Mixed Reality

I collegamenti diretti 3D (secondaryTiles) possono essere creati solo mentre la visualizzazione viene visualizzata in un visore WINDOWS MIXED REALITY visore VR. Quando la visualizzazione non viene presentata in un visore VR Windows Mixed Reality, è consigliabile gestila normalmente nascondendo il punto di ingresso o visualizzando un messaggio di errore. È possibile verificare questo risultato tramite una query [su IsCurrentViewPresentedOnHolographic().](/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_)

## <a name="tile-notifications"></a>Notifiche dei riquadri

Le notifiche dei riquadri attualmente non supportano l'invio di un aggiornamento con un asset 3D. Ciò significa che gli sviluppatori non possono eseguire le operazioni seguenti:

* Notifiche push
* Polling periodico
* Notifiche pianificate

Per altre informazioni sulle altre funzionalità e attributi dei riquadri e su come vengono usati per i riquadri 2D, vedere la documentazione riquadri per le [app UWP.](/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles)

## <a name="see-also"></a>Vedi anche

* [Esempio di modello di realtà mista](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) contenente un'utilità di avvio di app 3D.
* [Linee guida per la progettazione di utilità di avvio di app 3D](3d-app-launcher-design-guidance.md)
* [Creazione di modelli 3D da usare nella home Windows Mixed Reality home](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Implementazione di utilità di avvio di app 3D (app Win32)](implementing-3d-app-launchers-win32.md)
* [Esplorazione dello spazio iniziale di Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md)