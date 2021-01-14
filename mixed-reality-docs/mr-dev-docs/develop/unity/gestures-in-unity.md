---
title: Movimenti in Unity
description: Informazioni su come intervenire sullo sguardo in Unity con l'input del gesto manuale usando XR e le API comuni di pulsanti e assi.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: movimenti, Unity, sguardo, input, auricolare realtà mista, auricolare di realtà mista di Windows, cuffia virtuale reale, MRTK, Toolkit di realtà mista
ms.openlocfilehash: 2a968235abaeff9187580b7f5f77263b27c38c28
ms.sourcegitcommit: a1bb77f729ee2e0b3dbd1c2c837bb7614ba7b9bd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/14/2021
ms.locfileid: "98192958"
---
# <a name="gestures-in-unity"></a>Movimenti in Unity

Ci sono due modi principali per agire sullo [sguardo in Unity](gaze-in-unity.md), [movimenti della mano](../../design/gaze-and-commit.md#composite-gestures) e [controller di movimento](../../design/motion-controllers.md) in HoloLens e HMD immersivi. È possibile accedere ai dati per entrambe le origini dell'input spaziale tramite le stesse API in Unity.

Unity offre due modi principali per accedere ai dati di input spaziali per la realtà mista di Windows. Le API *input. GetButton/input. getaxis* comuni sono compatibili con più SDK di Unity XR, mentre l'API *InteractionManager/GestureRecognizer* specifica di Windows Mixed Reality espone il set completo di dati di input spaziali.

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a>API per movimenti compositi di alto livello (GestureRecognizer)

**Spazio dei nomi:** *UnityEngine. XR. WSA. input*<br>
**Tipi**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*

L'app può anche riconoscere movimenti compositi di livello superiore per le origini di input spaziali, i movimenti di tocco, di manipolazione e di navigazione. È possibile riconoscere questi movimenti compositi tra [le mani](../../design/gaze-and-commit.md#composite-gestures) e i [controller di movimento](../../design/motion-controllers.md) usando l'oggetto GestureRecognizer.

Ogni evento di movimento nell'oggetto GestureRecognizer fornisce SourceKind per l'input, nonché il raggio Head di destinazione al momento dell'evento. Alcuni eventi forniscono informazioni aggiuntive specifiche del contesto.

Sono necessari solo pochi passaggi per acquisire i movimenti usando un riconoscitore di movimento:
1. Creare un nuovo riconoscitore di movimento
2. Specificare i movimenti da controllare
3. Sottoscrivere gli eventi per questi movimenti
4. Avviare l'acquisizione di movimenti

### <a name="create-a-new-gesture-recognizer"></a>Creare un nuovo riconoscitore di movimento

Per utilizzare l'oggetto *GestureRecognizer*, è necessario avere creato un oggetto *GestureRecognizer*:

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a>Specificare i movimenti da controllare

Specificare i movimenti a cui si è interessati tramite *SetRecognizableGestures ()*:

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a>Sottoscrivere gli eventi per questi movimenti

Sottoscrivere gli eventi per i movimenti a cui si è interessati.

```cs
void Start()
{
    recognizer.Tapped += GestureRecognizer_Tapped;
    recognizer.HoldStarted += GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted += GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled += GestureRecognizer_HoldCanceled;
}
```

>[!NOTE]
>I movimenti di spostamento e manipolazione si escludono a vicenda in un'istanza di un oggetto *GestureRecognizer*.

### <a name="start-capturing-gestures"></a>Avviare l'acquisizione di movimenti

Per impostazione predefinita, un oggetto *GestureRecognizer* non monitora l'input fino a quando non viene chiamato *StartCapturingGestures ()* . È possibile che venga generato un evento di movimento dopo che è stato chiamato *StopCapturingGestures ()* se l'input è stato eseguito prima del frame in cui è stato elaborato *StopCapturingGestures ()* . L'oggetto *GestureRecognizer* ricorda se è stato acceso o disattivato durante il frame precedente in cui si è effettivamente verificato il movimento ed è quindi affidabile per avviare e arrestare il monitoraggio dei movimenti in base alla destinazione dello sguardo del frame.

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a>Interrompi acquisizione movimenti

Per arrestare il riconoscimento del movimento:

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a>Rimozione di un riconoscimento di movimento

Ricordarsi di annullare la sottoscrizione agli eventi sottoscritti prima di eliminare un oggetto *GestureRecognizer* .

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a>Rendering del modello di controller di movimento in Unity

![Modello e teleporting del controller di movimento](images/motioncontrollertest-teleport-1000px.png)<br>
*Modello e teleporting del controller di movimento*

Per eseguire il rendering dei controller di movimento nell'app che corrispondono ai controller fisici che gli utenti mantengono e si articolano con la pressione di vari pulsanti, è possibile usare la **prefabbricazione MotionController** nel [Toolkit di realtà mista](https://github.com/Microsoft/MixedRealityToolkit-Unity/).  Questa prefabbricata carica dinamicamente il modello glTF corretto in fase di esecuzione dal driver del controller di movimento installato dal sistema.  È importante caricare i modelli in modo dinamico, anziché importarli manualmente nell'editor, in modo che l'app visualizzi modelli 3D fisicamente accurati per i controller correnti e futuri che possono avere gli utenti.

1. Seguire le istruzioni [Introduzione](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) per scaricare il Toolkit di realtà mista e aggiungerlo al progetto Unity.
2. Se la fotocamera è stata sostituita con la prefabbricata *MixedRealityCameraParent* come parte del Introduzione passaggi, è possibile iniziare.  Il prefabbricato include il rendering del controller di movimento.  In caso contrario, aggiungere *assets/HoloToolkit/input/precasers/MotionControllers. prefabbricate* nella scena dal riquadro progetto.  È opportuno aggiungere tale prefabbricato come elemento figlio di qualsiasi oggetto padre utilizzato per spostare la fotocamera quando l'utente esegue il teleportamento all'interno della scena, in modo che i controller siano insieme all'utente.  Se l'app non implica il Teleporting, è sufficiente aggiungere il prefabbricato alla radice della scena.

## <a name="throwing-objects"></a>Generazione di oggetti

La generazione di oggetti in realtà virtuale è un problema più difficile rispetto a quello che può sembrare inizialmente. Come per la maggior parte delle interazioni basate fisicamente, quando la generazione di un gioco agisce in modo imprevisto, è immediatamente evidente e interrompe l'immersione. Abbiamo dedicato un po' di tempo a comprendere in modo approfondito come rappresentare un comportamento di generazione fisico corretto e avere a disposizione alcune linee guida, abilitate tramite aggiornamenti alla piattaforma, che vogliamo condividere con te.

È possibile trovare un esempio di come si consiglia di implementare il lancio [qui](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage). Questo esempio segue le quattro linee guida seguenti:
* **Utilizzare la *velocità* del controller invece della posizione**. Nell'aggiornamento di novembre di Windows è stata introdotta una modifica nel comportamento quando si [Verifica lo stato di rilevamento posizionale '' approssimativo](../../design/motion-controllers.md#controller-tracking-state). In questo stato, le informazioni sulla velocità del controller continueranno a essere segnalate fino a quando riteniamo che la sua accuratezza elevata, che è spesso più lunga della posizione, resta alta accuratezza.
* **Incorporare la *velocità angolare* del controller**. Questa logica è interamente contenuta nel `throwing.cs` file nel `GetThrownObjectVelAngVel` metodo statico, all'interno del pacchetto collegato sopra:
   1. Poiché viene mantenuta la velocità angolare, l'oggetto generato deve mantenere la stessa velocità angolare del momento in cui si trovava al momento della generazione: `objectAngularVelocity = throwingControllerAngularVelocity;`
   2. Poiché il centro della massa dell'oggetto generato è probabilmente diverso dall'origine della posizione del grip, è probabile che abbia una velocità diversa rispetto a quella del controller nel frame di riferimento dell'utente. La parte della velocità dell'oggetto contribuito in questo modo è la velocità tangenziale istantanea del centro della massa dell'oggetto generato intorno all'origine del controller. Questa velocità tangenziale è il prodotto incrociato della velocità angolare del controller con il vettore che rappresenta la distanza tra l'origine del controller e il centro della massa dell'oggetto generato.

      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```

   3. La velocità totale dell'oggetto generata è la somma della velocità del controller e della velocità tangenziale: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`

* **Prestare particolare attenzione all' *ora* in cui viene applicata la velocità**. Quando si preme un pulsante, l'evento può richiedere fino a 20 ms per la propagazione tramite Bluetooth al sistema operativo. Ciò significa che se si esegue il polling di una modifica dello stato del controller da Pressed a not Pressed o viceversa, il controller pone le informazioni che verranno apportate in precedenza in questa modifica dello stato. Inoltre, la formula del controller presentata dall'API di polling viene stimata in modo da riflettere un probabile posto nel momento in cui verrà visualizzato il frame che potrebbe essere più di 20 ms in futuro. Questo è ideale per il *rendering* degli oggetti conservati, ma costituisce un problema di tempo per la *destinazione* dell'oggetto durante il calcolo della traiettoria nel momento in cui l'utente ha rilasciato il Throw. Fortunatamente, con l'aggiornamento di novembre, quando viene inviato un evento Unity, ad esempio *InteractionSourcePressed* o *InteractionSourceReleased* , lo stato include i dati di post cronologici da indietro quando il pulsante è stato premuto o rilasciato.  Per ottenere il rendering del controller più accurato e la destinazione del controller durante i lanci, è necessario usare correttamente il polling e la gestione degli eventi, in base alle esigenze:
   * Per il **rendering del controller** ogni frame, l'app deve posizionare il *GameObject* del controller in corrispondenza del controller con stima avanzata per l'ora del fotone del frame corrente.  Si ottengono questi dati dalle API di polling Unity, ad esempio *[XR. InputTracking. GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* o *[XR. WSA. Input. InteractionManager. GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.
   * Per il **controller che punta** alla stampa o al rilascio, l'app deve Raycast e calcolare le traiettorie in base alla definizione del controller cronologico per l'evento di stampa o di rilascio.  Si ottengono questi dati dalle API di gestione degli eventi di Unity, ad esempio *[InteractionManager. InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.
* **Utilizzare la disposizione del grip**. La velocità e la velocità angolari vengono segnalate rispetto alla posizione del grip, non alla posizione del puntatore.

La generazione continuerà a migliorare con gli aggiornamenti futuri di Windows e ci si aspetterà di trovare altre informazioni su di essa.

## <a name="gesture-and-motion-controllers-in-mrtk-v2"></a>Controller movimento e movimento in MRTK V2

È possibile accedere a gesture e Motion controller dal gestore di input.
* [Movimento in MRTK V2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Gestures.html)
* [Controller di movimento in MRTK V2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Controllers.html)


## <a name="follow-along-with-tutorials"></a>Seguire le esercitazioni

Le esercitazioni dettagliate, con esempi di personalizzazione più dettagliati, sono disponibili in Mixed Reality Academy:

- [Input MR 211: Movimento](tutorials/holograms-211.md)
- [Input MR 213: Controller del movimento](../../deprecated/mixed-reality-213.md)

[![Input MR 213-controller di movimento](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)<br>
*Input MR 213-controller di movimento*

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si sta seguendo il percorso di sviluppo di Unity, si sta per esplorare i blocchi predefiniti di MRTK core. Da qui, è possibile passare al blocco predefinito successivo:

> [!div class="nextstepaction"]
> [Tracciamento della mano e oculare](hand-eye-in-unit.md)

In alternativa, passare alle API e funzionalità della piattaforma di realtà mista:

> [!div class="nextstepaction"]
> [Esperienze condivise](shared-experiences-in-unity.md)

È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#2-core-building-blocks) in qualsiasi momento.

## <a name="see-also"></a>Vedere anche

* [Puntamento con la testa e commit](../../design/gaze-and-commit.md)
* [Controller del movimento](../../design/motion-controllers.md)
