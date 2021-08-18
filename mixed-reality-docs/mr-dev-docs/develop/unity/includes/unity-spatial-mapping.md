---
ms.openlocfilehash: 271116683c94e051f61b78c0db3974ee843afdbd
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "121905703"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)

## <a name="spatial-awareness-system"></a>Sistema di consapevolezza spaziale

Per informazioni sulla configurazione [](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) di diversi osservatori della mesh spaziale, vedere la guida introduttiva alla consapevolezza spaziale.

Per informazioni sugli osservatori su dispositivo, vedere la guida [Configuring mesh observers for device (Configurazione di osservatori](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/configuring-spatial-awareness-mesh-observer) mesh per dispositivi).

Per informazioni sugli osservatori di comprensione della scena, vedere la Guida agli osservatori [di comprensione della](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/scene-understanding) scena.

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)

## <a name="armeshmanager"></a>ARMeshManager

ARFoundation di Unity fornisce un componente ARMeshManager per la visualizzazione incorporata delle mesh spaziali. Per [altre informazioni sull'utilizzo,](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/mesh-manager.html) vedere la documentazione di Unity.

## <a name="xrmeshsubsystem"></a>XRMeshSubsystem

Se si preferisce usare direttamente [XRMeshSubsystem](https://docs.unity3d.com/ScriptReference/XR.XRMeshSubsystem.html) di Unity, vedere la documentazione di Unity per altre informazioni [sull'utilizzo.](https://docs.unity3d.com/Manual/xrsdk-meshing.html)

## <a name="windows-xr-plugin"></a>Windows Plug-in XR

Windows Il plug-in XR offre alcuni metodi di estensione aggiuntivi per la configurazione di XRMeshSubsystem, ad esempio l'impostazione di una sfera di delimitazione o l'accesso alla rappresentazione della mesh della piattaforma sottostante. Tutte queste altre estensioni sono disponibili [nella documentazione di Unity.](https://docs.unity3d.com/Packages/com.unity.xr.windowsmr@5.3/api/UnityEngine.XR.WindowsMR.WindowsMRExtensions.html)

# <a name="legacy-wsa"></a>[Legacy WSA](#tab/wsa)

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a>Introduzione ai componenti di mapping spaziale predefiniti di Unity

Unity offre due componenti per aggiungere facilmente il mapping spaziale all'app: **Spatial Mapping Renderer (Renderer** di mapping spaziale) e Spatial Mapping **Collider (Collisore di mapping spaziale).**

### <a name="spatial-mapping-renderer"></a>Renderer di mapping spaziale

Il renderer di mapping spaziale consente di visualizzare la mesh di mapping spaziale.

![Renderer di mapping spaziale in Unity](../images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a>Collisore di mapping spaziale

Il collisore di mapping spaziale consente l'interazione di contenuto olografico (o carattere), ad esempio fisica, con la mesh di mapping spaziale.

![Spatial Mapping Collider in Unity](../images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a>Uso dei componenti di mapping spaziale predefiniti

È possibile aggiungere entrambi i componenti all'app se si desidera visualizzare e interagire con le superfici fisiche.

Per usare questi due componenti nell'app Unity:

1. Selezionare un GameObject al centro dell'area in cui si desidera rilevare le mesh della superficie spaziale.
2. Nella finestra Inspector (Controllo) **add Component**  >  **XR** Spatial Mapping Collider (Collisore di mapping spaziale XR  >     componente) **o Spatial Mapping Renderer (Renderer mapping spaziale).**

Per altre informazioni su come usare questi componenti, vedere il sito della <a href="https://docs.unity3d.com/2018.4/Documentation/Manual/SpatialMappingComponents.html" target="_blank">documentazione di Unity.</a>

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a>Oltre i componenti di mapping spaziale predefiniti

Questi componenti semplificano l'introduzione al mapping spaziale con il trascinamento della selezione. Per andare oltre, è possibile esplorare due percorsi principali:

* Per eseguire la propria elaborazione mesh di livello inferiore, vedere la sezione seguente sull'API script di mapping spaziale di basso livello.
* Per eseguire un'analisi mesh di livello superiore, vedere la sezione seguente sulla libreria SpatialUnderstanding in [MixedRealityToolkit.](https://github.com/microsoft/MixedRealityToolkit/tree/master/SpatialUnderstanding)

## <a name="using-the-low-level-unity-spatial-mapping-api"></a>Uso dell'API di mapping spaziale di Unity di basso livello

Se è necessario un maggiore controllo rispetto ai componenti Spatial Mapping Renderer (Renderer mapping spaziale) e Spatial Mapping Collider (Collisore di mapping spaziale), usare le API di mapping spaziale di basso livello.

**Spazio dei nomi:** *UnityEngine.XR.WSA*<br>
**Tipi:** *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*

Nelle sezioni seguenti è stato descritto il flusso suggerito per un'applicazione che usa le API di mapping spaziale.

### <a name="set-up-the-surfaceobservers"></a>Configurare SurfaceObserver

Creare un'istanza di un oggetto SurfaceObserver per ogni area di spazio definita dall'applicazione per cui sono necessari dati di mapping spaziale.

```cs
SurfaceObserver surfaceObserver;

private void Start()
{
    surfaceObserver = new SurfaceObserver();
}
```

Specificare l'area di spazio per cui ogni oggetto SurfaceObserver fornisce i dati chiamando SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox o SetVolumeAsFrustum. È possibile ridefinire l'area di spazio in futuro chiamando di nuovo uno di questi metodi.

```cs
private void Start()
{
    surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

Quando chiami SurfaceObserver.Update(), devi fornire un gestore per ogni superficie spaziale nell'area di spazio di SurfaceObserver per cui il sistema di mapping spaziale ha nuove informazioni. Il gestore riceve per una superficie spaziale:

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
{
    // see Handling Surface Changes
}
```

### <a name="handling-surface-changes"></a>Gestione delle modifiche della superficie

Esistono diversi casi principali da gestire: aggiunti e aggiornati, che possono usare lo stesso percorso di codice e rimossi.

* Nei casi aggiunti e aggiornati si aggiunge o si ottiene il GameObject che rappresenta questa mesh dal dizionario. Creiamo uno struct SurfaceData con i componenti necessari, quindi chiamiamo RequestMeshDataAsync per popolare GameObject con i dati della mesh e quindi lo posizioniamo nella scena.
* Nel caso rimosso, il GameObject che rappresenta questa mesh viene rimosso dal dizionario ed eliminato definitivamente.

```cs
System.Collections.Generic.Dictionary<SurfaceId, GameObject> spatialMeshObjects =
    new System.Collections.Generic.Dictionary<SurfaceId, GameObject>();

private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
{
    switch (changeType)
    {
        case SurfaceChange.Added:
        case SurfaceChange.Updated:
            if (!spatialMeshObjects.ContainsKey(surfaceId))
            {
                spatialMeshObjects[surfaceId] = new GameObject("spatial-mapping-" + surfaceId);
                spatialMeshObjects[surfaceId].transform.parent = this.transform;
                spatialMeshObjects[surfaceId].AddComponent<MeshRenderer>();
            }
            GameObject target = spatialMeshObjects[surfaceId];
            SurfaceData sd = new SurfaceData(
                // the surface id returned from the system
                surfaceId,
                // the mesh filter that is populated with the spatial mapping data for this mesh
                target.GetComponent<MeshFilter>() ?? target.AddComponent<MeshFilter>(),
                // the world anchor used to position the spatial mapping mesh in the world
                target.GetComponent<WorldAnchor>() ?? target.AddComponent<WorldAnchor>(),
                // the mesh collider that is populated with collider data for this mesh, if true is passed to bakeMeshes below
                target.GetComponent<MeshCollider>() ?? target.AddComponent<MeshCollider>(),
                // triangles per cubic meter requested for this mesh
                1000,
                // bakeMeshes - if true, the mesh collider is populated, if false, the mesh collider is empty.
                true
            );

            SurfaceObserver.RequestMeshAsync(sd, OnDataReady);
            break;
        case SurfaceChange.Removed:
            var obj = spatialMeshObjects[surfaceId];
            spatialMeshObjects.Remove(surfaceId);
            if (obj != null)
            {
                GameObject.Destroy(obj);
            }
            break;
        default:
            break;
    }
}
```

### <a name="handling-data-ready"></a>Gestione dei dati pronti

Il gestore OnDataReady riceve un oggetto SurfaceData. Gli oggetti WorldAnchor, MeshFilter e (facoltativamente) MeshCollider che contiene riflettono lo stato più recente della superficie spaziale associata. Facoltativamente, analizzare e/o [elaborare](../../../design/spatial-mapping.md#mesh-processing) i dati della mesh accedendo al membro Mesh dell'oggetto MeshFilter. Eseguire il rendering della superficie spaziale con la mesh più recente e (facoltativamente) usarla per collisioni fisiche e raycast. È importante verificare che il contenuto di SurfaceData non sia Null.

### <a name="start-processing-on-updates"></a>Avviare l'elaborazione degli aggiornamenti

SurfaceObserver.Update() deve essere chiamato in un ritardo, non in ogni fotogramma.

```cs
void Start ()
{
    StartCoroutine(UpdateLoop());
}

IEnumerator UpdateLoop()
{
    var wait = new WaitForSeconds(2.5f);
    while (true)
    {
        surfaceObserver.Update(OnSurfaceChanged);
        yield return wait;
    }
}
```
