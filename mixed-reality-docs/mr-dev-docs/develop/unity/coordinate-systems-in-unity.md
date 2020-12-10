---
title: Sistemi di coordinate in Unity
description: Scopri come creare esperienze di realtà mista, in piedi, in scala e in scala mondiale in Unity.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: sistema di coordinate, sistema di coordinate spaziali, solo orientamento, scalabilità verticale e scalabilità verticale scalabilità orizzontale, scala mondiale, 360 gradi, seduto, in piedi, stanza, mondo, scala, posizione, orientamento, Unity, ancoraggio, ancoraggio spaziale, ancoraggio globale, blocco globale, blocco globale, blocco corpo, blocco del corpo, perdita di rilevamento, locatability, limiti, recenter, auricolare realtà mista, cuffia a realtà mista, auricolare di realtà virtuale
ms.openlocfilehash: 900c393bf9ab09f1ac49e3108488d081f8025c19
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010282"
---
# <a name="coordinate-systems-in-unity"></a>Sistemi di coordinate in Unity

La realtà mista di Windows supporta le app in un'ampia gamma di [scale di esperienza](../../design/coordinate-systems.md), da app di solo orientamento e scalabilità verticale fino ad app a scalabilità. In HoloLens è possibile proseguire e creare app su scala mondiale che consentono agli utenti di superare i 5 metri, esplorando un'intera superficie di un edificio e oltre.

Il primo passaggio per creare un'esperienza di realtà mista in Unity consiste nel determinare quale [scalabilità dell'esperienza](../../design/coordinate-systems.md) sarà destinata all'app.

## <a name="building-an-orientation-only-or-seated-scale-experience"></a>Creazione di un'esperienza di solo orientamento o con scalabilità verticale

**Spazio dei nomi:** *UnityEngine. XR*<br>
**Tipo:** *XRDevice*

Per creare un'esperienza di **solo orientamento** o **scalabilità**, è necessario impostare Unity sul tipo di spazio di rilevamento stazionario. Lo spazio di rilevamento fisso imposta il sistema di Coordinate internazionali di Unity per tenere traccia del [frame di riferimento fisso](../../design/coordinate-systems.md#spatial-coordinate-systems). Nella modalità di rilevamento fisso, il contenuto inserito nell'editor appena davanti alla posizione predefinita della fotocamera (avanti è-Z) verrà visualizzato davanti all'utente all'avvio dell'app.

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

**Spazio dei nomi:** *UnityEngine. XR*<br>
**Tipo:** *InputTracking*

Per un' **esperienza solo con orientamento** puro, ad esempio un visualizzatore video di 360 gradi (dove gli aggiornamenti delle intestazioni posizionali potrebbero rovinare l'illusione), è possibile impostare [XR. InputTracking. disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) su true:

```cs
InputTracking.disablePositionalTracking = true;
```

Per un' **esperienza a scalabilità verticale**, per consentire all'utente di ricentrare l'origine in un secondo momento, è possibile chiamare [XR. Metodo InputTracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) :

```cs
InputTracking.Recenter();
```

## <a name="building-a-standing-scale-or-room-scale-experience"></a>Creazione di un'esperienza di scalabilità o scalabilità in base all'ambiente

**Spazio dei nomi:** *UnityEngine. XR*<br>
**Tipo:** *XRDevice*

Per un'esperienza **di scalabilità o** **scalabilità**, è necessario inserire il contenuto relativo alla superficie. Si ragiona sul pavimento dell'utente usando la **[fase spaziale](../../design/coordinate-systems.md#spatial-coordinate-systems)**, che rappresenta l'origine di livello del piano definita dall'utente e il limite di spazio facoltativo, configurato durante la prima esecuzione.

Per assicurarsi che Unity stia operando con il sistema di coordinate globale a livello di piano, è possibile impostare e verificare che Unity usi il tipo di spazio di rilevamento RoomScale:

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```
* Se SetTrackingSpaceType restituisce true, Unity ha cambiato correttamente il sistema di coordinate globali per tenere traccia del [frame della fase di riferimento](../../design/coordinate-systems.md#spatial-coordinate-systems).
* Se SetTrackingSpaceType restituisce false, Unity non è stato in grado di passare al frame della fase di riferimento, probabilmente perché l'utente non ha configurato un piano nel proprio ambiente. Anche se un valore restituito false non è comune, può verificarsi se la fase è configurata in un'altra stanza e il dispositivo viene spostato nella stanza corrente senza che l'utente configurasse una nuova fase.

Quando l'app imposta correttamente il tipo di spazio di rilevamento RoomScale, il contenuto inserito sul piano y = 0 verrà visualizzato sul pavimento. L'origine a 0, 0, 0 corrisponderà alla posizione specifica del piano in cui l'utente si trovava durante l'installazione della stanza, con-Z che rappresenta la direzione in avanti durante l'installazione.

**Spazio dei nomi:** *UnityEngine. EXPERIMENTal. XR*<br>
**Tipo:** *limite*

Nel codice di script è quindi possibile chiamare il metodo TryGetGeometry sul tipo UnityEngine. Experimental. XR. Boundary per ottenere un poligono di limiti, specificando un tipo di limite di TrackedArea. Se l'utente ha definito un limite (si ottiene un elenco di vertici), è possibile fornire all'utente un' **esperienza di scalabilità della stanza** , in cui è possibile aggirare la scena creata.

> [!NOTE]
> Il sistema eseguirà automaticamente il rendering del limite quando l'utente si avvicina. L'app non deve usare questo poligono per eseguire il rendering del limite. Tuttavia, è possibile scegliere di disporre gli oggetti della scena utilizzando questo poligono di limiti, per garantire che l'utente possa raggiungere fisicamente tali oggetti senza effettuare il Teleporting:

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a>Creazione di un'esperienza su scala globale

**Spazio dei nomi:** *UnityEngine. XR. WSA*<br>
**Tipo:** *WorldAnchor*

Per esperienze reali su **scala mondiale** su HoloLens che consentono agli utenti di superare i 5 metri, sono necessarie nuove tecniche oltre a quelle usate per le esperienze su scala. Una tecnica chiave da usare consiste nel creare un [ancoraggio spaziale](../../design/coordinate-systems.md#spatial-anchors) per bloccare un cluster di ologrammi con precisione sul posto nel mondo fisico, indipendentemente dalla distanza di roaming dell'utente e quindi [ritrovare gli ologrammi nelle sessioni successive](../../design/coordinate-systems.md#spatial-anchor-persistence).

In Unity si crea un ancoraggio spaziale aggiungendo il componente **WorldAnchor** Unity a un GameObject.

### <a name="adding-a-world-anchor"></a>Aggiunta di un ancoraggio globale

Per aggiungere un ancoraggio globale, chiamare AddComponent <WorldAnchor> () sull'oggetto Game con la trasformazione che si vuole ancorare nel mondo reale.

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

Ecco fatto! Questo oggetto Game verrà ora ancorato alla posizione corrente nel mondo fisico. è possibile che le coordinate internazionali del mondo Unity vengano modificate leggermente nel tempo per garantire l'allineamento fisico. Usare la [persistenza](persistence-in-unity.md) per trovare nuovamente questa posizione ancorata in una sessione di app futura.

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

## <a name="sharing-anchors-across-devices"></a>Condivisione di ancoraggi tra dispositivi

Usare gli <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">ancoraggi spaziali di Azure</a> per creare un ancoraggio cloud durevole da un WorldAnchor locale, che può essere individuato dall'app in più dispositivi HoloLens, iOS e Android.  Condividendo un ancoraggio spaziale comune tra più dispositivi, ogni utente può visualizzare il contenuto di cui è stato eseguito il rendering relativo a tale ancoraggio nella stessa posizione fisica.  Ciò rende possibili esperienze condivise in tempo reale.

Per iniziare a creare esperienze condivise in Unity, provare le <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">guide introduttive Unity Anchors di Azure</a>di 5 minuti.

Quando si è operativi con i Anchor spaziali di Azure, è possibile <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">creare e individuare ancoraggi in Unity</a>.

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si sta seguendo il percorso di checkpoint per lo sviluppo di Unity, è possibile esplorare i blocchi predefiniti di base della realtà mista. Da qui è possibile passare al blocco predefinito successivo:

> [!div class="nextstepaction"]
> [Sguardo fisso](gaze-in-unity.md)

In alternativa, passare alle API e funzionalità della piattaforma di realtà mista:

> [!div class="nextstepaction"]
> [Esperienze condivise](shared-experiences-in-unity.md)

È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#2-core-building-blocks) in qualsiasi momento.

## <a name="see-also"></a>Vedere anche
* [Scale Experience](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [Fase spaziale](../../design/coordinate-systems.md#stage-frame-of-reference)
* [Perdita del rilevamento in Unity](tracking-loss-in-unity.md)
* [Ancoraggi nello spazio](../../design/spatial-anchors.md)
* [Persistenza in Unity](persistence-in-unity.md)
* [Esperienze condivise in Unity](shared-experiences-in-unity.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Ancoraggi nello spazio di Azure</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK per Unity</a>
