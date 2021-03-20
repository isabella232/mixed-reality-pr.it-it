---
ms.openlocfilehash: 05e2b87383bbc91b7fd8785230152e3549f4b22d
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104719896"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

Il plug-in di OpenXR realtà mista fornisce la funzionalità di ancoraggio di base tramite un'implementazione di ARFoundation **ARAnchorManager** di Unity. Per informazioni sulle nozioni di base su ARAnchors in ARFoundation, vedere il [Manuale di ARFoundation per AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html). 

# <a name="unity-20192020--windows-xr-plugin"></a>[Plug-in Unity 2019/2020 + Windows XR](#tab/winxr)

Il plug-in di OpenXR realtà mista fornisce la funzionalità di ancoraggio di base tramite un'implementazione di ARFoundation **ARAnchorManager** di Unity. Per informazioni sulle nozioni di base su ARAnchors in ARFoundation, vedere il [Manuale di ARFoundation per AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).

# <a name="legacy-wsa"></a>[WSA legacy](#tab/wsa)

## <a name="building-a-world-scale-experience"></a>Creazione di un'esperienza su scala globale

**Spazio dei nomi:** *UnityEngine. XR. WSA*<br>
**Tipo:** *WorldAnchor*

Per esperienze reali su **scala mondiale** su HoloLens che consentono agli utenti di superare i 5 metri, sono necessarie nuove tecniche oltre a quelle usate per le esperienze su scala. Una tecnica chiave da usare consiste nel creare un [ancoraggio spaziale](../../../design/coordinate-systems.md#spatial-anchors) per bloccare un cluster di ologrammi con precisione sul posto nel mondo fisico, indipendentemente dalla distanza di roaming dell'utente e quindi [ritrovare gli ologrammi nelle sessioni successive](../../../design/coordinate-systems.md#spatial-anchor-persistence).

In Unity si crea un ancoraggio spaziale aggiungendo il componente **WorldAnchor** Unity a un GameObject.

### <a name="adding-a-world-anchor"></a>Aggiunta di un ancoraggio globale

Per aggiungere un ancoraggio globale, chiamare `AddComponent<WorldAnchor>()` sull'oggetto gioco con la trasformazione che si vuole ancorare nel mondo reale.

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

Questo è tutto. Questo oggetto Game verrà ora ancorato alla posizione corrente nel mondo fisico. è possibile che le coordinate internazionali del mondo Unity vengano modificate leggermente nel tempo per garantire l'allineamento fisico. Per trovare nuovamente questa posizione ancorata in una sessione di app futura, vedere [caricamento di un ancoraggio globale](#loading-a-worldanchor) .

### <a name="removing-a-world-anchor"></a>Rimozione di un ancoraggio globale

Se non si vuole più che il GameObject sia bloccato in una posizione fisica del mondo e non si intende trasferirlo in questo frame, è possibile chiamare semplicemente Destroy nel componente World Anchor.

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

Se si vuole spostare il GameObject in questo frame, è necessario chiamare DestroyImmediate.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a>Trasferimento di una GameObject ancorata globale

Non è possibile spostare GameObject mentre è presente un ancoraggio globale. Se è necessario spostare il GameObject di questo frame, è necessario:

1. DestroyImmediate il componente di ancoraggio globale
2. Spostare il GameObject
3. Aggiungere un nuovo componente di ancoraggio globale a GameObject.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a>Gestione delle modifiche apportate a Locatability

Un WorldAnchor non può essere locatable nel mondo fisico in un determinato momento. In tal caso, Unity non aggiornerà la trasformazione dell'oggetto ancorato. Questo può cambiare anche durante l'esecuzione di un'app. Se non si gestisce la modifica in locatability, l'oggetto non verrà visualizzato nella posizione fisica corretta del mondo.

Per ricevere notifiche sulle modifiche apportate a locatability:

1. Sottoscrivere l'evento OnTrackingChanged
2. Gestisci evento

L'evento **OnTrackingChanged** verrà chiamato ogni volta che l'ancoraggio spaziale sottostante viene modificato tra uno stato di locatable e non locatable.

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

Gestire quindi l'evento:

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

Talvolta gli ancoraggi si trovano immediatamente. In questo caso, la proprietà individuata dell'ancoraggio verrà impostata su true quando AddComponent <WorldAnchor> () restituisce. Di conseguenza, l'evento OnTrackingChanged non verrà attivato. Un modello pulito consiste nel chiamare il gestore OnTrackingChanged con lo stato individuato iniziale dopo aver collegato un ancoraggio.

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```