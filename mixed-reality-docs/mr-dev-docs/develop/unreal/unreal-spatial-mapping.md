---
title: Mapping spaziale in Unreal
description: Guida all'uso del mapping spaziale in Unreal
author: hferrone
ms.author: jacksonf
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, sviluppo, funzionalità, documentazione, guide, ologrammi, mapping spaziale, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale
ms.openlocfilehash: bde5a1b53f6ad90bc84f54bd3e4f1237b78f2abe
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609422"
---
# <a name="spatial-mapping-in-unreal"></a>Mapping spaziale in Unreal

Il mapping spaziale consente di posizionare gli oggetti sulle superfici fisiche del mondo reale. Quando viene eseguito il mapping dell'ambiente intorno a HoloLens, gli ologrammi sembrano più realistici per l'utente. Il mapping spaziale ancora gli oggetti nell'ambiente dell'utente sfruttando i suggerimenti di profondità e dando l'impressione che questi ologrammi si trovino effettivamente nello spazio. Gli ologrammi che fluttuano nello spazio o che si muovono insieme all'utente non vengono percepiti come reali, quindi è sempre necessario inserire gli elementi per comodità quando possibile.

Per altre informazioni su qualità del mapping spaziale, posizionamento, occlusione, rendering e così via, consulta il documento [Mapping spaziale](../../design/spatial-mapping.md).

## <a name="enabling-spatial-mapping"></a>Abilitazione del mapping spaziale

Per abilitare il mapping spaziale in HoloLens:
- Apri **Edit > Project Settings** (Modifica > Impostazioni progetto) e scorri fino alla sezione **Platforms** (Piattaforme).    
    + Seleziona **HoloLens** e **Spatial Perception** (Percezione spaziale).

![Screenshot delle funzionalità delle impostazioni di progetto di HoloLens con l'opzione Spatial Perception evidenziata](images/unreal-spatial-mapping-img-01.png)

Per acconsentire esplicitamente al mapping spaziale ed eseguire il debug di **MRMesh** in un gioco HoloLens:
1. Apri **ARSessionConfig** ed espandi la sezione **ARSettings > World Mapping** (ARSettings > Mapping mondo). 

2. Seleziona **Generate Mesh Data from Tracked Geometry** (Genera dati mesh da geometria rilevata), che indica al plug-in di HoloLens di avviare l'acquisizione asincrona dei dati di mapping spaziale e presentarli ad Unreal tramite **MRMesh**. 
3. Seleziona **Render Mesh Data in Wireframe** (Esegui il rendering dei dati mesh in wireframe) per visualizzare un contorno wireframe bianco di ogni triangolo in **MRMesh**. 

![Archivio di ancoraggi nello spazio pronto](images/unreal-spatialmapping-arsettings.PNG)


## <a name="spatial-mapping-at-runtime"></a>Mapping spaziale in fase di runtime
Puoi modificare i parametri seguenti per aggiornare il comportamento di runtime del mapping spaziale:

- Aprire **Edit > Project Settings** (Modifica > Impostazioni progetto), scorrere verso il basso fino alla sezione **Platforms** (Piattaforme) e selezionare **HoloLens > Spatial Mapping** (HoloLens > Mapping spaziale): 

![Impostazioni del progetto di ancoraggi nello spazio](images/unreal-spatialmapping-projectsettings.PNG)

- Il parametro **Max Triangles Per Cubic Meter** (Numero massimo di triangoli per metro cubo) aggiorna la densità dei triangoli nella mesh di mapping spaziale.  
- Il parametro **Spatial Meshing Volume Size** (Dimensioni del volume della mesh spaziale) indica le dimensioni del cubo intorno al giocatore per il rendering e l'aggiornamento dei dati di mapping spaziale.  
    + Se prevedi che l'ambiente di runtime dell'applicazione sia di grandi dimensioni, è possibile che questo valore debba essere elevato per poter corrispondere allo spazio reale. Il valore può essere più piccolo se l'applicazione deve soltanto posizionare ologrammi sulle superfici immediatamente attorno all'utente. Il volume di mapping spaziale si sposterà quindi contestualmente all'utente. 

## <a name="working-with-mrmesh"></a>Uso di MRMesh

In primo luogo, è necessario avviare il mapping spaziale:

![Progetto della funzione ToggleARCapture con il tipo di acquisizione Spatial Mapping evidenziato](images/unreal-spatial-mapping-img-02.png)

Una volta acquisito, è consigliabile disattivare il mapping spaziale per lo spazio.  Il mapping spaziale può essere completato dopo un determinato periodo di tempo oppure quando i raycast emessi in ogni direzione restituiscono collisioni con MRMesh.

Per ottenere l'accesso a **MRMesh** in fase di runtime:
1. Aggiungi un componente **ARTrackableNotify** a un attore del progetto. 

![Ancoraggi nello spazio AR Trackable Notify](images/unreal-spatialmapping-artrackablenotify.PNG)

2. Seleziona il componente **ARTrackableNotify** ed spandi la sezione **Events** (Events) nel pannello **Details** (Dettagli). 
    - Selezionare il pulsante **+** sugli eventi da monitorare. 

![Eventi sugli ancoraggi nello spazio](images/unreal-spatialmapping-events.PNG)

In questo caso viene monitorato l'evento **On Add Tracked Geometry** (All'aggiunta della geometria rilevata), che cerca mesh reali valide corrispondenti ai dati del mapping spaziale. L'elenco completo degli eventi è disponibile nell'API del componente [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html). 

Il materiale della mesh può essere modificato nel grafico eventi del progetto o in C++. Nello screenshot seguente è mostrato il percorso del progetto: 

![Esempi di ancoraggi nello spazio](images/unreal-spatialmapping-example.PNG)

## <a name="spatial-mapping-in-c"></a>Mapping spaziale in C++

Nel file build.cs del gioco aggiungere **AugmentedReality** e **MRMesh** all'elenco PublicDependencyModuleNames:

```cpp
PublicDependencyModuleNames.AddRange(
    new string[] {
        "Core",
        "CoreUObject",
        "Engine",
        "InputCore",    
        "EyeTracker",
        "AugmentedReality",
        "MRMesh"
});
```

Per accedere a MRMesh, effettuare la sottoscrizione ai delegati **OnTrackableAdded**:

```cpp
#include "ARBlueprintLibrary.h"
#include "MRMeshComponent.h"

void AARTrackableMonitor::BeginPlay()
{
    Super::BeginPlay();

    // Subscribe to Tracked Geometry delegates
    UARBlueprintLibrary::AddOnTrackableAddedDelegate_Handle(
        FOnTrackableAddedDelegate::CreateUObject(this, &AARTrackableMonitor::OnTrackableAdded)
    );
}

void AARTrackableMonitor::OnTrackableAdded(UARTrackedGeometry* Added)
{
    // When tracked geometry is received, check that it's from spatial mapping
    if(Added->GetObjectClassification() == EARObjectClassification::World)
    {
        UMRMeshComponent* MRMesh = Added->GetUnderlyingMesh();
    }
}
```

> [!NOTE]
> Sono presenti delegati simili per eventi aggiornati e rimossi, rispettivamente **AddOnTrackableUpdatedDelegate_Handle** e **AddOnTrackableRemovedDelegate_Handle**.
>
> L'elenco completo degli eventi è disponibile nell'API [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html).

## <a name="see-also"></a>Vedere anche
* [Mapping spaziale](../../design/spatial-mapping.md)
