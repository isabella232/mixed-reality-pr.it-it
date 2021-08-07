---
title: Movimenti in Unity
description: Informazioni su come intervenire sullo sguardo fisso in Unity con l'input del movimento della mano usando XR e api comuni per pulsanti e assi.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: movimenti, unity, sguardo fisso, input, visore VR di realtà mista, visore VR windows di realtà mista, visore VR di realtà virtuale, MRTK, realtà mista Toolkit
ms.openlocfilehash: 8dd6b64dd0bb52e64515a43d69713ecc5dc6bcec203a987568f7c25ac492a864
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214764"
---
# <a name="gestures-in-unity"></a>Movimenti in Unity

Esistono due modi chiave per intervenire sullo [](../../design/gaze-and-commit.md#composite-gestures) sguardo [fisso in Unity,](gaze-in-unity.md)i movimenti delle mani e i controller del movimento [in](../../design/motion-controllers.md) HoloLens immersive. È possibile accedere ai dati per entrambe le origini di input spaziale tramite le stesse API in Unity.

Unity offre due modi principali per accedere ai dati di input spaziali per Windows Mixed Reality. Le API *comuni Input.GetButton/Input.GetAxis* funzionano in più SDK XR unity, mentre l'API *InteractionManager/GestureRecognizer* specifica di Windows Mixed Reality espone il set completo di dati di input spaziali.

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a>API per movimenti compositi di alto livello (GestureRecognizer)

**Spazio dei nomi:** *UnityEngine.XR.WSA.Input*<br>
**Tipi:** *GestureRecognizer,* *GestureSettings,* *InteractionSourceKind*

L'app può anche riconoscere i movimenti compositi di livello superiore per le origini di input spaziali, i movimenti Tocco, Tieni premuto, Manipolazione e Navigazione. È possibile riconoscere questi movimenti compositi su [mani e](../../design/gaze-and-commit.md#composite-gestures) controller [del movimento](../../design/motion-controllers.md) usando GestureRecognizer.

Ogni evento Gesture in GestureRecognizer fornisce SourceKind per l'input e il raggio della testa di destinazione al momento dell'evento. Alcuni eventi forniscono informazioni aggiuntive specifiche del contesto.

Per acquisire i movimenti con un sistema di riconoscimento movimenti sono necessari solo alcuni passaggi:
1. Creare un nuovo riconoscitore movimenti
2. Specificare i movimenti da controllare
3. Sottoscrivere eventi per tali movimenti
4. Avviare l'acquisizione dei movimenti

### <a name="create-a-new-gesture-recognizer"></a>Creare un nuovo riconoscitore movimenti

Per usare *GestureRecognizer,* è necessario aver creato *un oggetto GestureRecognizer:*

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a>Specificare i movimenti da controllare

Specificare i movimenti a cui si è interessati tramite *SetRecognizableGestures():*

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a>Sottoscrivere eventi per tali movimenti

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
>I movimenti di navigazione e manipolazione si escludono a vicenda in un'istanza di *un oggetto GestureRecognizer.*

### <a name="start-capturing-gestures"></a>Avviare l'acquisizione dei movimenti

Per impostazione predefinita, *GestureRecognizer non monitora* l'input fino a quando non viene chiamato *StartCapturingGestures().* È possibile che venga generato un evento di movimento dopo la chiamata a *StopCapturingGestures()* se l'input è stato eseguito prima del frame in cui è stato elaborato *StopCapturingGestures().* *GestureRecognizer* ricorda se era attivo o spento durante il fotogramma precedente in cui si è effettivamente verificato il movimento ed è quindi affidabile avviare e arrestare il monitoraggio del movimento in base alla destinazione dello sguardo fisso di questo fotogramma.

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a>Interrompere l'acquisizione dei movimenti

Per arrestare il riconoscimento dei movimenti:

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a>Rimozione di un sistema di riconoscimento movimenti

Ricordarsi di annullare la sottoscrizione agli eventi sottoscritti prima di eliminare un *oggetto GestureRecognizer.*

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a>Rendering del modello di controller del movimento in Unity

![Modello di controller del movimento e teletrasporto](images/motioncontrollertest-teleport-1000px.png)<br>
*Modello di controller del movimento e teletrasporto*

Per eseguire il rendering dei controller del movimento nell'app che corrispondono ai controller fisici che gli utenti sono in possesso e articolano man mano che vengono premuti vari [pulsanti,](https://github.com/Microsoft/MixedRealityToolkit-Unity/)puoi usare il **prefab MotionController** in Mixed Reality Toolkit .  Questo prefab carica dinamicamente il modello glTF corretto in fase di esecuzione dal driver del controller del movimento installato del sistema.  È importante caricare questi modelli in modo dinamico anziché importarli manualmente nell'editor, in modo che l'app mostri modelli 3D fisicamente accurati per qualsiasi controller corrente e futuro degli utenti.

1. Segui le [Attività iniziali](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) seguenti per scaricare il Toolkit realtà mista e aggiungerlo al progetto Unity.
2. Se la fotocamera è stata sostituita con il prefab *MixedRealityCameraParent* come parte dei passaggi Attività iniziali, è possibile farlo.  Il prefab include il rendering del controller del movimento.  In caso contrario, aggiungere *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* nella scena dal Project azioni.  È necessario aggiungere il prefab come elemento figlio di qualsiasi oggetto padre che si usa per spostare la fotocamera quando l'utente teletrasporta all'interno della scena, in modo che i controller siano d'accordo con l'utente.  Se l'app non comporta il teletrasporto, è sufficiente aggiungere il prefab nella radice della scena.

## <a name="throwing-objects"></a>Generazione di oggetti

La generazione di oggetti nella realtà virtuale è un problema più difficile di quanto possa sembrare. Come per la maggior parte delle interazioni basate fisicamente, quando il lancio nel gioco agisce in modo imprevisto, è immediatamente ovvio e interrompe l'interazione. Abbiamo dedicato un po' di tempo a pensare a come rappresentare un comportamento di generazione fisicamente corretto e abbiamo creato alcune linee guida, abilitate tramite gli aggiornamenti della piattaforma, che microsoft vuole condividere con l'utente.

È possibile trovare un esempio di come è consigliabile implementare la generazione di [eccezioni qui.](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage) Questo esempio segue queste quattro linee guida:
* **Usare la velocità del *controller invece della* posizione**. Nell'aggiornamento di novembre Windows, è stata introdotta una modifica del comportamento quando si è nello stato di rilevamento [posizionale "Approssimativo".](../../design/motion-controllers.md#controller-tracking-state) In questo stato, le informazioni sulla velocità del controller continueranno a essere segnalate fino a quando si ritiene che l'accuratezza elevata, che spesso è più lunga della posizione, rimanga elevata.
* **Incorporare *la velocità angolare del* controller**. Questa logica è tutto contenuto nel file nel metodo statico, all'interno del pacchetto collegato in `throwing.cs` `GetThrownObjectVelAngVel` precedenza:
   1. Poiché la velocità angolare è conservata, l'oggetto generato deve mantenere la stessa velocità angolare che aveva al momento del lancio: `objectAngularVelocity = throwingControllerAngularVelocity;`
   2. Poiché il centro della massa dell'oggetto generato probabilmente non è all'origine della posizione del controllo, è probabile che abbia una velocità diversa rispetto a quella del controller nel frame di riferimento dell'utente. La parte della velocità dell'oggetto che ha contribuito in questo modo è la velocità tangente istantanea del centro di massa dell'oggetto generato intorno all'origine del controller. Questa velocità tangente è il prodotto incrociato della velocità angolare del controller con il vettore che rappresenta la distanza tra l'origine del controller e il centro della massa dell'oggetto generato.

      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```

   3. La velocità totale dell'oggetto generato è la somma della velocità del controller e di questa velocità tangente: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`

* **Prestare particolare attenzione al *momento in* cui viene applicata la velocità**. Quando si preme un pulsante, l'evento può richiedere fino a 20 ms per Bluetooth al sistema operativo. Ciò significa che se si esegue il polling di una modifica dello stato del controller da premuta a non premuta o in altro modo, le informazioni sulla posizione del controller che si ottengono con saranno effettivamente in anticipo rispetto a questa modifica dello stato. Inoltre, la posizione del controller presentata dall'API di polling viene stimata in avanti per riflettere una posizione probabile nel momento in cui verrà visualizzato il fotogramma che potrebbe essere superiore a 20 ms in futuro. Ciò è valido per il *rendering* di oggetti  mantenuti, ma com contiene un problema di tempo per la destinazione dell'oggetto mentre si calcola la erretà per il momento in cui l'utente ha rilasciato il lancio. Fortunatamente, con l'aggiornamento di novembre, quando viene inviato un evento Unity come *InteractionSourcePressed* o *InteractionSourceReleased,* lo stato include i dati cronologici sulla posizione dalla posizione precedente quando il pulsante è stato premuto o rilasciato.  Per ottenere il rendering del controller più accurato e la destinazione del controller durante le eccezioni, è necessario usare correttamente il polling e l'evento, in base alle esigenze:
   * Per il rendering di ogni fotogramma da parte del **controller,** l'app deve posizionare il *GameObject* del controller in corrispondenza della posizione del controller stimata in avanti per il tempo di fotone del fotogramma corrente.  È possibile ottenere questi dati dalle API di polling di Unity come *[XR. InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* o *[XR. Wsa. Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.
   * Per **il controller che punta** a una press o a un rilascio, l'app deve eseguire il raycast e calcolare le erre in base alla posizione cronologica del controller per l'evento di stampa o rilascio.  Questi dati vengono visualizzati dalle API di gestione degli eventi di Unity, ad *[esempio InteractionManager.InteractionSourcePressed.](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*
* **Usare la posizione del controllo**. Angular la velocità e la velocità vengono segnalate in relazione alla posizione del controllo, non alla posizione del puntatore.

La generazione di eccezioni continuerà a migliorare con gli aggiornamenti Windows futuri e si prevede di trovare altre informazioni qui.

## <a name="gesture-and-motion-controllers-in-mrtk"></a>Movimenti e controller del movimento in MRTK

È possibile accedere al movimento e al controller del movimento da Gestione input.

* [Movimento in MRTK](/windows/mixed-reality/mrtk-unity/features/input/gestures)
* [Controller del movimento in MRTK](/windows/mixed-reality/mrtk-unity/features/input/controllers)

## <a name="follow-along-with-tutorials"></a>Seguire le esercitazioni

Esercitazioni dettagliate, con esempi di personalizzazione più dettagliati, sono disponibili in Mixed Reality Academy:

- [Input MR 211: Movimento](tutorials/holograms-211.md)
- [Input MR 213: Controller del movimento](../../deprecated/mixed-reality-213.md)

[![Input MR 213 - Controller del movimento](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)<br>
*Input MR 213 - Controller del movimento*

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si sta seguendo il percorso di sviluppo di Unity che è stato strutturato, si stanno esplorando i blocchi predefiniti principali di MRTK. Da qui è possibile passare al blocco predefinito successivo:

> [!div class="nextstepaction"]
> [Tracciamento della mano e oculare](./hand-eye-in-unity.md)

In alternativa, passare alle API e funzionalità della piattaforma di realtà mista:

> [!div class="nextstepaction"]
> [Esperienze condivise](shared-experiences-in-unity.md)

È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#2-core-building-blocks) in qualsiasi momento.

## <a name="see-also"></a>Vedere anche

* [Puntamento con la testa e commit](../../design/gaze-and-commit.md)
* [Controller del movimento](../../design/motion-controllers.md)