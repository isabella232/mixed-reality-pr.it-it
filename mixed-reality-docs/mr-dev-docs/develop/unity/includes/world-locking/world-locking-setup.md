---
ms.openlocfilehash: 047a77259d78ba8ea68002a5142080971900e305
ms.sourcegitcommit: 6f3b3aa31cc3acefba5fa3ac3ba579d9868a4fe4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/31/2021
ms.locfileid: "123244283"
---
# <a name="world-locking-tools-recommended"></a>[Strumenti di blocco del mondo (scelta consigliata)](#tab/wlt)

È consigliabile installare World Locking Tools usando il nuovo strumento di funzionalità di realtà mista. Dopo aver scaricato Mixed Reality Feature Tool dal collegamento seguente, selezionare la versione più recente di **WLT Core** nella **sezione World Locking Tools (Strumenti** di blocco del mondo):

![Finestra di selezione delle funzionalità di Mixed Reality Feature Tool con gli strumenti di blocco del mondo selezionati](../../images/spatial-anchors-setup-img-01.png)

> [!div class="nextstepaction"]
> [Installare world locking tools con mr feature tool](../../welcome-to-mr-feature-tool.md)

### <a name="automated-setup"></a>Configurazione automatizzata

Quando il progetto è pronto per l'avvio, eseguire l'utilità di configurazione della scena da **Mixed Reality > World Locking Tools:**

![Editor unity con il menu Toolkit realtà mista selezionato](../../images/world-locking-configuration-img-01.jpeg)

> [!IMPORTANT]
> L'utilità Configura scena può essere rieseguita in qualsiasi momento. Ad esempio, deve essere rieseguita se la destinazione AR è stata modificata da Legacy a XR SDK. Se la scena è già configurata correttamente, l'esecuzione dell'utilità non ha alcun effetto.

### <a name="visualizers"></a>Visualizzatori

Durante lo sviluppo iniziale, l'aggiunta di visualizzatori può essere utile per assicurarsi che WLT sia configurato e funzioni correttamente. Possono essere rimossi per le prestazioni di produzione o, se per qualsiasi motivo non sono più necessari, usando l'utilità Rimuovi visualizzatori. Altri dettagli sui visualizzatori sono disponibili nella documentazione [degli strumenti](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/Tools.html#visualizers).

# <a name="aranchormanager"></a>[ARAnchorManager](#tab/anchorstore)

Il plug-in OpenXR di realtà mista fornisce funzionalità di ancoraggio di base tramite un'implementazione di ARFoundation **ARAnchorManager di** Unity. Per apprendere le nozioni di base su ARAnchors in ARFoundation, visita il manuale [arFoundation per AR Anchor Manager.](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html) 

# <a name="worldanchor"></a>[WorldAnchor](#tab/worldanchor)

## <a name="building-a-world-scale-experience"></a>Creazione di un'esperienza su scala globale

**Spazio dei nomi:** *UnityEngine.XR.WSA*<br>
**Tipo:** *WorldAnchor*

Per esperienze su scala **reale** in HoloLens che consentono agli utenti di andare oltre i 5 metri, sono necessarie nuove tecniche oltre a quelle usate per le esperienze in locale. Una tecnica chiave da usare consiste [](../../../../design/coordinate-systems.md#spatial-anchors) nel creare un ancoraggio nello spazio per bloccare un cluster di ologrammi esattamente sul posto nel mondo fisico, indipendentemente dalla distanza in cui l'utente ha percorso il roaming, e quindi trovare di nuovo gli [ologrammi](../../../../design/coordinate-systems.md#spatial-anchor-persistence)nelle sessioni successive.

In Unity si crea un ancoraggio nello spaziale aggiungendo il **componente WorldAnchor** Unity a un GameObject.

### <a name="adding-a-world-anchor"></a>Aggiunta di un ancoraggio mondo

Per aggiungere un ancoraggio del mondo, chiama `AddComponent<WorldAnchor>()` sull'oggetto gioco con la trasformazione che vuoi ancorare nel mondo reale.

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

Questo è tutto. Questo oggetto gioco verrà ora ancorato alla posizione corrente nel mondo fisico. È possibile che le coordinate del mondo Unity si aggiegano leggermente nel tempo per garantire l'allineamento fisico. Fare riferimento a [Caricare un ancoraggio del](#loading-a-worldanchor) mondo per trovare di nuovo questa posizione ancorata in una sessione futura dell'app.

### <a name="removing-a-world-anchor"></a>Rimozione di un ancoraggio mondo

Se non vuoi più che il GameObject sia bloccato in una posizione fisica e non intendi spostarlo in questo frame, puoi semplicemente chiamare Destroy (Distruggi) sul componente World Anchor (Ancoraggio mondo).

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

Se vuoi spostare il GameObject in questo frame, devi invece chiamare DestroyImmediate.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a>Spostamento di un GameObject ancorato al mondo

Gli oggetti GameObject non possono essere spostati mentre è in esso un ancoraggio del mondo. Se è necessario spostare il GameObject in questo frame, è necessario:

1. DestroyImmediate the World Anchor component
2. Spostare il GameObject
3. Aggiungere un nuovo componente World Anchor (Ancoraggio mondo) a GameObject.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a>Gestione delle modifiche di individuabilità

Un WorldAnchor potrebbe non essere localizzato nel mondo fisico in un momento nel tempo. In questo caso, Unity non aggiorrerà la trasformazione dell'oggetto ancorato. Questo può cambiare anche durante l'esecuzione di un'app. Se non si gestisce la modifica dell'individuabilità, l'oggetto non verrà visualizzato nella posizione fisica corretta nel mondo.

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