---
ms.openlocfilehash: f937b705f10cc4a287600349283ecaed4ae44666
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112908113"
---
# <a name="world-locking-tools-recommended"></a>[Strumenti di blocco del mondo (scelta consigliata)](#tab/wlt)

Per impostazione predefinita, World Locking Tools ripristina il sistema di coordinate di Unity rispetto al mondo fisico tra le sessioni. Ciò significa che per fare in modo che un ologramma venga visualizzato nello stesso luogo nel mondo fisico dopo aver quitting e rieseguiti l'applicazione, l'ologramma deve avere di nuovo la stessa posizione.

![Componente del contesto di blocco del mondo in Unity Inspector](../../images/world-locking-tools-img-02.png)

Se l'applicazione richiede un controllo  più **fine,** il salvataggio automatico e il caricamento automatico possono essere disabilitati nel controllo e la persistenza può essere gestita da uno script come descritto nella sezione relativa alla persistenza della [documentazione](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/Concepts/Advanced/Persistence.html).

# <a name="aranchormanager"></a>[ARAnchorManager](#tab/anchorstore)

Un'API aggiuntiva denominata **XRAnchorStore consente** di rendere persistenti gli ancoraggi tra le sessioni. XRAnchorStore è una rappresentazione degli ancoraggi salvati in un dispositivo. Gli ancoraggi possono essere resi persistenti dagli **ARAnchor** nella scena Unity, caricati dalla memoria in nuovi **ARAnchor** o eliminati dalla memoria.

> [!NOTE]
> Questi ancoraggi devono essere salvati e caricati nello stesso dispositivo. L'archiviazione tra dispositivi di ancoraggio sarà supportata tramite Ancoraggi nello spazio di Azure in una versione futura.

### <a name="namespaces"></a>Spazi dei nomi

Per **Unity 2020 e OpenXR:** 

``` cs
using Microsoft.MixedReality.ARSubsystems.XRAnchorStore
```

o **Unity 2019/2020 + Plug-in Windows XR:** 

```cs 
using UnityEngine.XR.WindowsMR.XRAnchorStore
```

### <a name="public-methods"></a>Metodi pubblici

```cs 
{
    // A list of all persisted anchors, which can be loaded.
    public IReadOnlyList<string> PersistedAnchorNames { get; }

    // Clear all persisted anchors
    public void Clear();

    // Load a single persisted anchor by name. The ARAnchorManager will create this new anchor and report it in
    // the ARAnchorManager.anchorsChanged event. The TrackableId returned here is the same TrackableId the
    // ARAnchor will have when it is instantiated.
    public TrackableId LoadAnchor(string name);

    // Attempts to persist an existing ARAnchor with the given TrackableId to the local store. Returns true if
    // the storage is successful, false otherwise.
    public bool TryPersistAnchor(TrackableId id, string name);

    // Removes a single persisted anchor from the anchor store. This will not affect any ARAnchors in the Unity
    // scene, only the anchors in storage.
    public void UnpersistAnchor(string name);
}
```

### <a name="getting-an-anchor-store-reference"></a>Recupero di un riferimento a un archivio di ancoraggi 

Per caricare XRAnchorStore con **Unity 2020 e OpenXR,** usare il metodo di estensione nel sottosistema XRAnchorSubsystem di un ARAnchorManager:

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

Per caricare XRAnchorStore con **Unity 2019/2020 e il plug-in Windows XR,** usare il metodo di estensione in XRReferencePointSubsystem (Unity 2019) o XRAnchorSubsystem (Unity 2020), il sottosistema di un ARReferencePointManager/ARAnchorManager:

```cs
// Unity 2019 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem);

// Unity 2020 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem);
```

### <a name="loading-an-anchor-store"></a>Caricamento di un archivio di ancoraggio

Per caricare un archivio di ancoraggio in **Unity 2020 e OpenXR,** accedervi dal sottosistema di arAnchorManager come indicato di seguito:

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

o con **Unity 2019/2020 e il plug-in Windows XR:**

``` cs
// Unity 2019
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();

// Unity 2020
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

Per un esempio completo di ancoraggi persistenti/non persistenti, vedi lo script Anchors -> Anchors Sample GameObject e AnchorsSample.cs nella scena di esempio del plug-in [OpenXR](../../xr-project-setup.md#unity-sample-projects-for-openxr-and-hololens-2)di Realtà mista:

![Screenshot del pannello della gerarchia aperto nell'editor di Unity con l'esempio di ancoraggi evidenziato](../../images/openxr-features-img-04.png)

![Screenshot del pannello di controllo aperto nell'editor di Unity con lo script di esempio degli ancoraggi evidenziato](../../images/openxr-features-img-05.png)

# <a name="worldanchor"></a>[WorldAnchor](#tab/worldanchor)

**WorldAnchorStore è** la chiave per creare esperienze olografiche in cui gli ologrammi rimangono in posizioni reali specifiche tra le istanze dell'applicazione. Gli utenti possono quindi aggiungere singoli ologrammi dove vogliono e trovarli in un secondo momento nello stesso punto in molti usi dell'app.

**Spazio dei nomi:** *UnityEngine.XR.WSA.Persistence*<br>
**Classe:** *WorldAnchorStore*

WorldAnchorStore consente di rendere persistente la posizione di WorldAnchor tra le sessioni. Per rendere effettivamente persistenti gli ologrammi tra le sessioni, dovrai tenere traccia separatamente dei GameObject che usano un ancoraggio mondo specifico. Spesso è opportuno creare una radice GameObject con un ancoraggio del mondo e avere ologrammi figlio ancorati con un offset di posizione locale.

Per caricare gli ologrammi dalle sessioni precedenti:

1. Ottenere WorldAnchorStore
2. Caricare i dati dell'app relativi all'ancoraggio del mondo, che fornisce l'ID dell'ancoraggio del mondo
3. Caricare un ancoraggio del mondo dal relativo ID

Per salvare gli ologrammi per sessioni future:

1. Ottenere WorldAnchorStore
2. Salvare un ancoraggio mondo specificando un ID
3. Salvare i dati dell'app relativi all'ancoraggio del mondo insieme a un ID

### <a name="getting-the-worldanchorstore"></a>Recupero di WorldAnchorStore

È necessario mantenere un riferimento a WorldAnchorStore in modo da sapere quando è pronto per eseguire un'operazione. Poiché si tratta di una chiamata asincrona, potenzialmente non appena si avvia, si vuole chiamare:

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

StoreLoaded in questo caso è il gestore per quando WorldAnchorStore ha completato il caricamento:

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

È ora disponibile un riferimento a WorldAnchorStore, che verrà utilizzato per salvare e caricare ancoraggi del mondo specifici.

### <a name="saving-a-worldanchor"></a>Salvataggio di un Oggetto WorldAnchor

Per salvare, è sufficiente assegnare un nome a ciò che si sta salvando e passarlo all'oggetto WorldAnchor ottenuto in precedenza quando si vuole salvare. Nota: il tentativo di salvare due ancoraggi nella stessa stringa avrà esito negativo (archiviare. Save restituirà false). Eliminare il salvataggio precedente prima di salvare quello nuovo:

```cs
private void SaveGame()
{
    // Save data about holograms positioned by this world anchor
    if (!this.savedRoot) // Only Save the root once
    {
           this.savedRoot = this.store.Save("rootGameObject", anchor);
           Assert(this.savedRoot);
    }
}
```

### <a name="loading-a-worldanchor"></a>Caricamento di un WorldAnchor

E per caricare:

```cs
private void LoadGame()
{
    // Save data about holograms positioned by this world anchor
    this.savedRoot = this.store.Load("rootGameObject", rootGameObject);
    if (!this.savedRoot)
    {
        s// We didn't actually have the game root saved! We have to re-place our objects or start over
    }
}
```

È anche possibile usare lo Store. Delete() per rimuovere un ancoraggio salvato e salvato in precedenza. Clear() per rimuovere tutti i dati salvati in precedenza.

### <a name="enumerating-existing-anchors"></a>Enumerazione degli ancoraggi esistenti

Per individuare gli ancoraggi archiviati in precedenza, chiamare GetAllIds.

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a>Persistenza degli ologrammi per più dispositivi

È possibile usare Ancoraggi nello stato di <a href="/azure/spatial-anchors/overview" target="_blank">Azure</a> per creare un ancoraggio cloud durevole da un WorldAnchor locale, che l'app può quindi individuare in più dispositivi HoloLens, iOS e Android, anche se questi dispositivi non sono presenti contemporaneamente.  Poiché gli ancoraggi nel cloud sono persistenti, più dispositivi nel tempo possono visualizzare il rendering del contenuto relativo a tale ancoraggio nella stessa posizione fisica.

Per iniziare a creare esperienze condivise in Unity, provare le guide introduttive di Unity per Ancoraggi nello spazio di Azure di 5 <a href="/azure/spatial-anchors/unity-overview" target="_blank">minuti.</a>

Quando si è in esecuzione con Ancoraggi nello spazio di Azure, è possibile creare e individuare <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">ancoraggi in Unity.</a>