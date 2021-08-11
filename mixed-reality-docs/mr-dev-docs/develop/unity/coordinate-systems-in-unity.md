---
title: Sistemi di coordinate in Unity
description: Informazioni su come creare esperienze di realtà mista, in piedi, su scala locale e su scala mondiale in Unity.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: sistema di coordinate, sistema di coordinate spaziali, solo orientamento, scala da seduti, scalabilità in piedi, scalabilità locale, scala globale, 360 gradi, seduti, in piedi, stanza, scala, scala, posizione, orientamento, Unity, ancoraggio spaziale, ancoraggio globale, world-locked, world-locking, body-locked, body-locking, tracking loss, locatability, bounds, recenter, mixed reality headset, visore di realtà mista windows, visore realtà virtuale
ms.openlocfilehash: 3372b9bd259202145fd658e225a36d2125f4a86d01eb90bc765b65918540db8b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203583"
---
# <a name="coordinate-systems-in-unity"></a>Sistemi di coordinate in Unity

Windows Mixed Reality supporta le app in un'ampia gamma di scalabilità di esperienze, dalle app con orientamento solo e da seduti fino alle app su larga scala. In HoloLens, è possibile andare oltre e creare app di livello mondiale che consentono agli utenti di superare i 5 metri, esplorando un intero piano di un edificio e oltre.

Il primo passaggio per creare un'esperienza di realtà mista in Unity consiste nel comprendere i sistemi di coordinate e scegliere la [scalabilità dell'esperienza](../../design/coordinate-systems.md) a cui l'app sarà destinazione.

## <a name="building-an-orientation-only-or-seated-scale-experience"></a>Creazione di un'esperienza solo orientamento o su scala da seduti

**Spazio dei nomi:** *UnityEngine.XR*<br>
**Tipo:** *XRDevice*

Per creare **un'esperienza solo orientamento** o su scala da seduti, è necessario impostare Unity sul tipo di spazio di rilevamento stazionario.  Lo spazio di rilevamento stazionario imposta il sistema di coordinate del mondo di Unity per tenere traccia [del fotogramma stazionario di riferimento.](../../design/coordinate-systems.md#spatial-coordinate-systems) Nella modalità di rilevamento stazionario, il contenuto posizionato nell'editor proprio davanti alla posizione predefinita della fotocamera (forward è -Z) verrà visualizzato davanti all'utente all'avvio dell'app.

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

**Spazio dei nomi:** *UnityEngine.XR*<br>
**Tipo:** *InputTracking*

Per **un'esperienza** pura solo con orientamento, ad esempio un visualizzatore video a 360 gradi (in cui gli aggiornamenti della testa posizionale avrebbero distrutto l'illusione), è quindi possibile impostare [XR. InputTracking.disablePositionalTracking su](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) true:

```cs
InputTracking.disablePositionalTracking = true;
```

Per **un'esperienza su larga scala,** per consentire all'utente di eseguire in seguito una versione più recente dell'origine da seduti, è possibile chiamare [il metodo XR. Metodo InputTracking.Recenter:](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)

```cs
InputTracking.Recenter();
```

## <a name="building-a-standing-scale-or-room-scale-experience"></a>Creazione di un'esperienza su larga scala o su scala locale

**Spazio dei nomi:** *UnityEngine.XR*<br>
**Tipo:** *XRDevice*

Per **un'esperienza su larga** **scala** o su scala locale, è necessario posizionare il contenuto rispetto al piano. Il piano dell'utente viene ragione usando la fase spaziale **[,](../../design/coordinate-systems.md#spatial-coordinate-systems)** che rappresenta l'origine definita a livello di piano dell'utente e il limite facoltativo della stanza, configurato durante la prima esecuzione.

Per garantire il funzionamento di Unity con il sistema di coordinate globale a livello di piano, è possibile impostare e testare che Unity sta usando il tipo di spazio di rilevamento RoomScale:

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
* Se SetTrackingSpaceType restituisce true, Unity ha commutato correttamente il sistema di coordinate del mondo per tenere traccia del [fotogramma della fase di riferimento.](../../design/coordinate-systems.md#spatial-coordinate-systems)
* Se SetTrackingSpaceType restituisce false, Unity non è stato in grado di passare al frame di fase di riferimento, probabilmente perché l'utente non ha configurato un piano nel proprio ambiente. Anche se un valore restituito falso non è comune, può verificarsi se la fase è impostata in una stanza diversa e il dispositivo viene spostato nella stanza corrente senza che l'utente configura una nuova fase.

Dopo che l'app ha impostato correttamente il tipo di spazio di rilevamento RoomScale, sul piano y=0 verrà visualizzato il contenuto posizionato sul piano y=0. L'origine a 0, 0, 0 sarà la posizione specifica sul piano in cui si trovava l'utente durante la configurazione della stanza, con -Z che rappresenta la direzione in avanti che stava affrontando durante la configurazione.

**Spazio dei nomi:** *UnityEngine.Experimental.XR*<br>
**Tipo:** *Limite*

Nel codice di script è quindi possibile chiamare il metodo TryGetGeometry sul tipo UnityEngine.Experimental.XR.Boundary per ottenere un poligono limite, specificando un tipo di limite TrackedArea. Se l'utente ha definito un limite (si ottiene un elenco di  vertici), è possibile offrire un'esperienza su larga scala all'utente, in cui può aggirare la scena creata.

> [!NOTE]
> Il sistema eseguirà automaticamente il rendering del limite quando l'utente vi si avvicina. L'app non deve usare questo poligono per eseguire il rendering del limite stesso. Tuttavia, è possibile scegliere di impostare il layout degli oggetti della scena usando questo poligono limite, per garantire che l'utente possa raggiungere fisicamente tali oggetti senza teletrasporto:

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a>Creazione di un'esperienza su scala globale

**Spazio dei nomi:** *UnityEngine.XR.WSA*<br>
**Tipo:** *WorldAnchor*

Per le **vere esperienze su** scala HoloLens che consentono agli utenti di superare i 5 metri, sono necessarie nuove tecniche oltre a quelle usate per le esperienze su larga scala. Una tecnica chiave da usare consiste nel creare un [ancoraggio](../../design/coordinate-systems.md#spatial-anchors) spaziale per bloccare un cluster di ologrammi esattamente in posizione nel mondo fisico, indipendentemente dalla distanza di roaming dell'utente e quindi trovare di nuovo tali [ologrammi](../../design/coordinate-systems.md#spatial-anchor-persistence)nelle sessioni successive.

In Unity si crea un ancoraggio spaziale aggiungendo il **componente WorldAnchor** Unity a gameobject.

### <a name="adding-a-world-anchor"></a>Aggiunta di un ancoraggio world

Per aggiungere un ancoraggio mondo, chiamare AddComponent () sull'oggetto gioco con la trasformazione che si vuole ancorare <WorldAnchor> nel mondo reale.

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

Questo è tutto. Questo oggetto di gioco sarà ora ancorato alla posizione corrente nel mondo fisico. È possibile che le coordinate del mondo unity si aggireranno leggermente nel tempo per garantire l'allineamento fisico. Usare [la persistenza](persistence-in-unity.md) per trovare di nuovo questa posizione ancorata in una sessione futura dell'app.

### <a name="removing-a-world-anchor"></a>Rimozione di un ancoraggio mondo

Se non si vuole più che GameObject venga bloccato in una posizione fisica del mondo e non si intende spostarlo in questo frame, è sufficiente chiamare Destroy sul componente World Anchor.

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

Se si vuole spostare GameObject in questo frame, è invece necessario chiamare DestroyImmediate.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a>Spostamento di un oggetto GameObject ancorato al mondo

Gli oggetti GameObject non possono essere spostati mentre è in esecuzione un ancoraggio mondo. Se è necessario spostare GameObject in questo frame, è necessario:
1. DestroyImmediate the World Anchor component
2. Spostare GameObject
3. Aggiungere un nuovo componente World Anchor a GameObject.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a>Gestione delle modifiche di individuazione

Un Oggetto WorldAnchor potrebbe non essere localizzato nel mondo fisico in un momento nel tempo. In questo caso, Unity non aggiorerà la trasformazione dell'oggetto ancorato. Questo può cambiare anche durante l'esecuzione di un'app. Se non si gestisce la modifica dell'individuazione, l'oggetto non verrà visualizzato nella posizione fisica corretta nel mondo.

Per ricevere una notifica sulle modifiche di individuazione:
1. Sottoscrivere l'evento OnTrackingChanged
2. Gestire l'evento

**L'evento OnTrackingChanged** verrà chiamato ogni volta che l'ancoraggio spaziale sottostante cambia tra uno stato di posizione e non di posizione.

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

Gestire quindi l'evento :

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

A volte gli ancoraggi si trovano immediatamente. In questo caso, la proprietà isLocated dell'ancoraggio verrà impostata su true quando viene restituito AddComponent <WorldAnchor> (). Di conseguenza, l'evento OnTrackingChanged non verrà attivato. Un modello pulito potrebbe essere chiamare il gestore OnTrackingChanged con lo stato IsLocated iniziale dopo aver collegato un ancoraggio.

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="sharing-anchors-across-devices"></a>Condivisione di ancoraggi tra dispositivi

Usare <a href="/azure/spatial-anchors/overview" target="_blank">Ancoraggi nello</a> spaziale di Azure per creare un ancoraggio cloud durevole da un WorldAnchor locale, che l'app può quindi individuare in più dispositivi HoloLens, iOS e Android.  Condividendo un ancoraggio spaziale comune tra più dispositivi, ogni utente può visualizzare il rendering del contenuto relativo all'ancoraggio nella stessa posizione fisica.  Ciò rende possibili esperienze condivise in tempo reale.

Per iniziare a creare esperienze condivise in Unity, provare le guide introduttive di <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity di</a>5 minuti.

Dopo aver eseguito le attività con Ancoraggi nello spazio di Azure, è possibile creare e individuare ancoraggi <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">in Unity.</a>

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si sta seguendo il percorso di checkpoint di sviluppo di Unity che è stato previsto, si stanno esplorando i blocchi predefiniti di base della realtà mista. Da qui è possibile passare al blocco predefinito successivo:

> [!div class="nextstepaction"]
> [Sguardo fisso](gaze-in-unity.md)

In alternativa, passare alle API e funzionalità della piattaforma di realtà mista:

> [!div class="nextstepaction"]
> [Esperienze condivise](shared-experiences-in-unity.md)

È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#2-core-building-blocks) in qualsiasi momento.

## <a name="see-also"></a>Vedere anche
* [Scale dell'esperienza](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [Fase spaziale](../../design/coordinate-systems.md#stage-frame-of-reference)
* [Perdita del rilevamento in Unity](tracking-loss-in-unity.md)
* [Ancoraggi nello spazio](../../design/spatial-anchors.md)
* [Persistenza in Unity](persistence-in-unity.md)
* [Esperienze condivise in Unity](shared-experiences-in-unity.md)
* <a href="/azure/spatial-anchors" target="_blank">Ancoraggi nello spazio di Azure</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK per Unity</a>