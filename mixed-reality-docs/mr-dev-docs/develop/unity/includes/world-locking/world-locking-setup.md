---
ms.openlocfilehash: 6229b258233f7a80ef6530edd6eb94774a0e54cf
ms.sourcegitcommit: 3e36b2fbbcc250c49aaf8ca1b6133cf0e9db69fa
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2021
ms.locfileid: "107528814"
---
# <a name="world-locking-tools-recommended"></a>[Strumenti di blocco del mondo (scelta consigliata)](#tab/wlt)

È consigliabile installare World Locking Tools usando il nuovo strumento di funzionalità di realtà mista. Dopo aver scaricato Mixed Reality Feature Tool dal collegamento seguente, selezionare la versione più recente di **WLT Core** nella **sezione World Locking Tools (Strumenti** di blocco del mondo):

![Finestra di selezione delle funzionalità di Mixed Reality Feature Tool con gli strumenti di blocco del mondo selezionati](../../images/spatial-anchors-setup-img-01.png)

> [!div class="nextstepaction"]
> [Installare world locking tools con mr feature tool](../../welcome-to-mr-feature-tool.md)

### <a name="automated-setup"></a>Configurazione automatizzata

Quando il progetto è pronto, eseguire l'utilità di configurazione della scena da **Mixed Reality Toolkit > Utilities > World Locking Tools:**

![Editor unity con il menu mixed reality toolkit selezionato](../../images/world-locking-configuration-img-01.jpeg)

> [!IMPORTANT]
> L'utilità Configura scena può essere rieseguita in qualsiasi momento. Ad esempio, deve essere rieseguita se la destinazione AR è stata modificata da Legacy a XR SDK. Se la scena è già configurata correttamente, l'esecuzione dell'utilità non ha alcun effetto.

### <a name="visualizers"></a>Visualizzatori

Durante lo sviluppo iniziale, l'aggiunta di visualizzatori può essere utile per assicurarsi che WLT sia configurato e funzioni correttamente. Possono essere rimossi per le prestazioni di produzione o se per qualsiasi motivo non sono più necessari, usando l'utilità Rimuovi visualizzatori. Altri dettagli sui visualizzatori sono disponibili nella documentazione [degli strumenti](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/Tools.html#visualizers).

# <a name="aranchormanager"></a>[ARAnchorManager](#tab/anchorstore)

Il plug-in OpenXR di realtà mista fornisce funzionalità di ancoraggio di base tramite un'implementazione di ARFoundation **ARAnchorManager di** Unity. Per informazioni di base su ARAnchors in ARFoundation, visita il manuale [arFoundation per AR Anchor Manager.](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html) 

# <a name="worldanchor"></a>[WorldAnchor](#tab/worldanchor)

## <a name="building-a-world-scale-experience"></a>Creazione di un'esperienza su scala globale

**Spazio dei nomi:** *UnityEngine.XR.WSA*<br>
**Tipo:** *WorldAnchor*

Per le **vere esperienze su** scala mondiale in HoloLens che consentono agli utenti di superare i 5 metri, sono necessarie nuove tecniche oltre quelle usate per le esperienze su larga scala. Una tecnica chiave da usare consiste nel creare un [ancoraggio](../../../../design/coordinate-systems.md#spatial-anchors) spaziale per bloccare un cluster di ologrammi esattamente in posizione nel mondo fisico, indipendentemente dalla distanza di roaming dell'utente e quindi trovare di nuovo tali [ologrammi](../../../../design/coordinate-systems.md#spatial-anchor-persistence)nelle sessioni successive.

In Unity si crea un ancoraggio spaziale aggiungendo il **componente WorldAnchor** Unity a gameobject.

### <a name="adding-a-world-anchor"></a>Aggiunta di un ancoraggio mondo

Per aggiungere un ancoraggio del mondo, chiamare `AddComponent<WorldAnchor>()` sull'oggetto di gioco con la trasformazione che si vuole ancorare nel mondo reale.

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

Questo è tutto. Questo oggetto di gioco sarà ora ancorato alla posizione corrente nel mondo fisico. È possibile che le coordinate del mondo unity si aggireranno leggermente nel tempo per garantire l'allineamento fisico. Fare riferimento a [Caricamento di un ancoraggio mondo](#loading-a-worldanchor) per trovare di nuovo questa posizione ancorata in una sessione futura dell'app.

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

Un Oggetto WorldAnchor potrebbe non essere localizzato nel mondo fisico in un momento nel tempo. In questo caso, Unity non aggiorerà la trasformazione dell'oggetto ancorato. Questo può cambiare anche durante l'esecuzione di un'app. Se non si gestisce la modifica dell'individuabilità, l'oggetto non verrà visualizzato nella posizione fisica corretta nel mondo.

Per ricevere notifiche sulle modifiche di individuabilità:

1. Sottoscrivere l'evento OnTrackingChanged
2. Gestire l'evento

**L'evento OnTrackingChanged** verrà chiamato ogni volta che l'ancoraggio nello spazio sottostante cambia tra uno stato di posizione e non di individuazione.

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

A volte gli ancoraggi si trovano immediatamente. In questo caso, questa proprietà isLocated dell'ancoraggio verrà impostata su true quando viene restituito AddComponent <WorldAnchor> (). Di conseguenza, l'evento OnTrackingChanged non verrà attivato. Un modello pulito sarebbe chiamare il gestore OnTrackingChanged con lo stato IsLocated iniziale dopo aver collegato un ancoraggio.

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```