---
title: EyeTracking_TargetSelection
description: Come accedere ai dati degli occhi e agli eventi specifici degli sguardi per selezionare le destinazioni in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, EyeTracking,
ms.openlocfilehash: 77fa5801d08805153c7d0476314be49f9cc41956
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104694168"
---
# <a name="eye-supported-target-selection"></a>Selezione della destinazione supportata dagli occhi

![Selezione destinazione MRTK](../Images/EyeTracking/mrtk_et_targetselect.png)

In questa pagina vengono illustrate diverse opzioni per l'accesso ai dati degli occhi e agli eventi specifici degli sguardi per selezionare le destinazioni in MRTK. Il rilevamento degli occhi consente selezioni di destinazione rapide e veloci utilizzando una combinazione di informazioni sugli elementi che un utente sta esaminando con input aggiuntivi, ad esempio il _rilevamento manuale_ e i _comandi vocali_:

- Osservare & pronunciare _"Select"_ (comando Voice predefinito)
- Look & Say _"Explode"_ o _"pop"_ (Custom Voice Commands)
- Cerca & pulsante Bluetooth
- Si osservi & pizzico (ad esempio, tenete la mano davanti all'utente e si riuniscono il pollice e l'indice)
  - Si noti che per il corretto funzionamento, [è necessario disabilitare i raggi della mano](EyeTracking_EyesAndHands.md#how-to-disable-the-hand-ray)

Per selezionare il contenuto olografico con Eye sguardi, sono disponibili diverse opzioni:

[**1. utilizzare il puntatore di stato attivo primario:**](#1-use-generic-focus-and-pointer-handlers)

Questo può essere considerato come il cursore con priorità.
Per impostazione predefinita, se le mani sono visualizzate, si tratta di raggi di mano.
Se non è presente alcuna mano, il puntatore con priorità è il punto di vista.
Si noti, quindi, che in base alla testa di progettazione corrente o allo sguardo occhi viene eliminato come input del cursore se vengono usati i raggi mano.

Ad esempio:

Un utente desidera selezionare un pulsante olografico remoto.
Gli sviluppatori desiderano fornire una soluzione flessibile che consenta all'utente di ottenere queste attività in diverse condizioni:

- Passare al pulsante e incuriosirlo
- Esaminarla da una distanza e pronunciare "Select"
- Come destinazione del pulsante usando un raggio di mano ed eseguendo un pizzicotto in questo caso, la soluzione più flessibile consiste nell'usare il gestore dello stato attivo primario, in quanto invierà una notifica ogni volta che il puntatore di stato attivo primario con priorità corrente attiva un evento. Si noti che se sono abilitati i raggi di mano, il puntatore a capo o a occhio è disabilitato non appena vengono visualizzate le lancette.

> [!IMPORTANT]
> Si noti che se sono abilitati i raggi di mano, il puntatore a capo o a occhio è disabilitato non appena vengono visualizzate le lancette. Se si vuole supportare un'interazione [ _"look and Pinch"_ , è necessario disabilitare il raggio di mano](EyeTracking_EyesAndHands.md#how-to-disable-the-hand-ray). Nelle scene di esempio di analisi degli occhi è stato disabilitato il raggio della mano per consentire la presentazione di interazioni più ricche con gli occhi e i movimenti di mano. vedere ad esempio [posizionamento con supporto oculare](EyeTracking_Positioning.md).

[**2. utilizzare lo stato attivo per gli occhi e i raggi della mano contemporaneamente:**](#2-independent-eye-gaze-specific-eyetrackingtarget)

Potrebbero essere presenti istanze in cui si desidera essere più specifici del tipo di puntatori di interesse che può attivare determinati eventi e consentire simultaneamente l'utilizzo di più tecniche di interazione a distanza.

Nell'app, ad esempio, un utente può usare raggi lontani per modificare alcune configurazioni meccaniche olografiche. ad esempio, afferrare e mantenere alcune parti del motore olografico distanti e mantenerle sul posto. Quando si esegue questa operazione, l'utente deve eseguire una serie di istruzioni e registrarne lo stato di avanzamento contrassegnando alcune caselle di controllo. Se l'utente ha le proprie mani _non occupate_, sarà istintivo toccare semplicemente la casella di controllo o selezionarla usando un raggio di mano. Tuttavia, se l'utente ha le sue mani occupate, come nel caso di alcune parti del motore olografiche, si desidera consentire all'utente di scorrere facilmente le istruzioni usando il proprio sguardo ed esaminare semplicemente una casella di controllo e pronunciare "check!".

Per abilitare questa operazione, è necessario usare uno script EyeTrackingTarget specifico per gli occhi, che è indipendente dal FocusHandlers Core MRTK e verrà illustrato più avanti.

## <a name="1-use-generic-focus-and-pointer-handlers"></a>1. utilizzare i gestori di puntatore e messa a fuoco generici

Se la verifica degli occhi è configurata correttamente (vedere il [programma di installazione di base di MRTK per l'uso degli](EyeTracking_BasicSetup.md)occhi), consentire agli utenti di selezionare gli ologrammi usando gli occhi è uguale a qualsiasi altro input dello stato attivo (ad esempio, lo sguardo a capo o il raggio della mano). Questo offre il grande vantaggio di un modo flessibile per interagire con gli ologrammi definendo il tipo di stato attivo principale nel profilo del puntatore di input di MRTK in base alle esigenze dell'utente, lasciando inalterato il codice. In questo modo è possibile passare da uno sguardo all'altro senza modificare una riga di codice o sostituire i raggi mano con la destinazione degli occhi per le interazioni.

### <a name="focusing-on-a-hologram"></a>Concentrarsi su un ologramma

Per rilevare quando un ologramma è concentrato, usare l'interfaccia _' IMixedRealityFocusHandler '_ che fornisce due membri di interfaccia: _OnFocusEnter_ e _OnFocusExit_.

Ecco un semplice esempio di [ColorTap. cs](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ColorTap) per modificare il colore di un ologramma quando si esamina.

```c#
public class ColorTap : MonoBehaviour, IMixedRealityFocusHandler
{
    void IMixedRealityFocusHandler.OnFocusEnter(FocusEventData eventData)
    {
        material.color = color_OnHover;
    }

    void IMixedRealityFocusHandler.OnFocusExit(FocusEventData eventData)
    {
        material.color = color_IdleState;
    }
    ...
}
```

### <a name="selecting-a-focused-hologram"></a>Selezione di un ologramma concentrato

Per selezionare un ologramma concentrato, usare _PointerHandler_ per restare in ascolto degli eventi di input per confermare una selezione.
Ad esempio, se si aggiunge _IMixedRealityPointerHandler_ , i reagenti reagiranno a un semplice input del puntatore.
L'interfaccia _IMixedRealityPointerHandler_ richiede l'implementazione dei tre membri di interfaccia seguenti: _OnPointerUp_, _OnPointerDown_ e _OnPointerClicked_.

Nell'esempio seguente viene modificato il colore di un ologramma guardandolo e pizzicando o dicendo "Select".
L'azione necessaria per attivare l'evento è definita `eventData.MixedRealityInputAction == selectAction` in base alla quale è possibile impostare il tipo di `selectAction` nell'editor di Unity. per impostazione predefinita, si tratta dell'azione "Select". I tipi di [MixedRealityInputActions](../Input/InputActions.md) disponibili possono essere configurati nel profilo MRTK tramite azioni di input di input del _profilo di configurazione di MRTK_  ->    ->  .

```c#
public class ColorTap : MonoBehaviour, IMixedRealityFocusHandler, IMixedRealityPointerHandler
{
    // Allow for editing the type of select action in the Unity Editor.
    [SerializeField]
    private MixedRealityInputAction selectAction = MixedRealityInputAction.None;
    ...

    void IMixedRealityPointerHandler.OnPointerUp(MixedRealityPointerEventData eventData)
    {
        if (eventData.MixedRealityInputAction == selectAction)
        {
            material.color = color_OnHover;
        }
    }

    void IMixedRealityPointerHandler.OnPointerDown(MixedRealityPointerEventData eventData)
    {
        if (eventData.MixedRealityInputAction == selectAction)
        {
            material.color = color_OnSelect;
        }
    }

    void IMixedRealityPointerHandler.OnPointerClicked(MixedRealityPointerEventData eventData) { }
}
```

### <a name="eye-gaze-specific-baseeyefocushandler"></a>BaseEyeFocusHandler specifici degli sguardi

Considerato che gli occhi possono essere molto diversi da quelli degli altri input del puntatore, è opportuno assicurarsi di reagire all'input dello stato attivo solo se si tratta di un' _occhiata_ e si tratta attualmente del puntatore di input primario.
A questo scopo, è necessario usare l'oggetto [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) specifico del rilevamento degli occhi e che deriva da [`BaseFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseFocusHandler) .
Come indicato in precedenza, viene attivato solo se il targeting degli occhi è l'input del puntatore principale (ovvero, non è attivo alcun raggio di mano). Per ulteriori informazioni, vedere [la pagina relativa alla modalità di supporto di sguardi a occhio e movimenti della mano](EyeTracking_EyesAndHands.md).

Di seguito è riportato un esempio di `EyeTrackingDemo-03-Navigation` (assets/MRTK/examples/Demos/eyetracking/scenes).
In questa demo sono presenti due ologrammi 3D che diventeranno a seconda della parte dell'oggetto da esaminare: se l'utente osserva il lato sinistro dell'ologramma, la parte verrà spostata lentamente verso l'inizio dell'utente.
Se si esamina il lato destro, la parte verrà spostata lentamente in primo piano.
Si tratta di un comportamento che potrebbe non essere necessario attivare in qualsiasi momento e anche qualcosa che potrebbe non essere necessario attivare accidentalmente da un raggio di mano o da uno sguardo a capo.
Con l'oggetto [`OnLookAtRotateByEyeGaze`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.OnLookAtRotateByEyeGaze) collegato, un GameObject verrà ruotato mentre viene esaminato.

```c#
public class OnLookAtRotateByEyeGaze : BaseEyeFocusHandler
{
    ...

    protected override void OnEyeFocusStay()
    {
        // Update target rotation
        RotateHitTarget();
    }

    ...

    ///
    /// This function computes the rotation of the target to move the currently
    /// looked at aspect slowly to the front.
    ///
    private void RotateHitTarget()
    {
        // Example for querying the hit position of the eye gaze ray using EyeGazeProvider
        Vector3 TargetToHit = (this.gameObject.transform.position - InputSystem.EyeGazeProvider.HitPosition).normalized;

        ...
    }
}
```

Consultare la documentazione dell'API per un elenco completo degli eventi disponibili di [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) :

- **OnEyeFocusStart:** Attivato dopo che il raggio d'occhio *inizia* a intersecarsi con questo Collider della destinazione.
- **OnEyeFocusStay:** Attivato *quando* il raggio di sguardi occhi si interseca con il Collider di questa destinazione.
- **OnEyeFocusStop:** Attivato quando il raggio di sguardi occhi *smette* di intersecarsi con questo Collider della destinazione.
- **OnEyeFocusDwell:** Attivato dopo che il raggio d'occhio è stato intersecato con il Collider della destinazione per un periodo di tempo specificato.

## <a name="2-independent-eye-gaze-specific-eyetrackingtarget"></a>2. EyeTrackingTarget specifici per gli occhi indipendenti

Infine, viene fornita una soluzione che consente di considerare l'input basato sugli occhi completamente indipendente dagli altri puntatori dello stato attivo tramite lo [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script.

Questa operazione presenta tre _vantaggi_:

- È possibile assicurarsi che l'ologramma stia reagendo solo sugli sguardi dell'utente.
- Questo è indipendente dall'input primario attualmente attivo. Di conseguenza, è possibile elaborare più input contemporaneamente, ad esempio, combinando il targeting rapido con i movimenti della mano.
- Molti eventi Unity sono già stati configurati in modo da velocizzare e semplificare la gestione e il riutilizzo dei comportamenti esistenti dall'editor di Unity o tramite codice.

Sono presenti anche alcuni _svantaggi:_

- Maggiore sforzo per gestire separatamente gli input separati.
- Nessun calo di eleganza: supporta solo l'individuazione degli occhi. Se la verifica degli occhi non funziona, è necessario un altro fallback.

Analogamente a _BaseFocusHandler_, _EyeTrackingTarget_ è pronto con diversi eventi Unity specifici degli sguardi che è possibile ascoltare comodamente tramite l'editor di Unity (vedere l'esempio seguente) o usando _AddListener ()_ nel codice:

- OnLookAtStart()
- WhileLookingAtTarget()
- OnLookAway()
- Ondweller ()
- OnSelected ()

Di seguito vengono illustrati alcuni esempi di come usare _EyeTrackingTarget_.

### <a name="example-1-eye-supported-smart-notifications"></a>Esempio di #1: notifiche intelligenti con supporto oculistico

In `EyeTrackingDemo-02-TargetSelection` (assets/MRTK/examples/Demos/eyetracking/scenes), è possibile trovare un esempio per _"notifiche attente intelligenti"_ che reagiscono a sguardi d'occhio.
Si tratta di caselle di testo 3D che possono essere posizionate nella scena e che aumenteranno in modo uniforme e si rivolgono all'utente quando vengono esaminate per semplificare la leggibilità. Mentre l'utente sta leggendo la notifica, le informazioni continuano a essere visualizzate in modo nitido e chiaro. Dopo la lettura e la visualizzazione della notifica, la notifica verrà eliminata automaticamente e verrà rilasciata. Per ottenere questo risultato, sono disponibili alcuni script di comportamento generici che non sono specifici del rilevamento degli occhi, ad esempio:

- [`FaceUser`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FaceUser)
- [`ChangeSize`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ChangeSize)
- [`BlendOut`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.BlendOut)

Il vantaggio di questo approccio è che gli stessi script possono essere riutilizzati da vari eventi. Un ologramma, ad esempio, può iniziare ad affrontare l'utente in base a comandi vocali o dopo aver premuto un pulsante virtuale. Per attivare questi eventi, è possibile fare riferimento semplicemente ai metodi che devono essere eseguiti nello [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script associato al GameObject.

Per l'esempio relativo alle _notifiche attente intelligenti_, si verifica quanto segue:

- **OnLookAtStart ()**: la notifica inizia con...
  - *FaceUser. Engage:* ... rivolgersi all'utente.
  - *ChangeSize. Engage:* ... aumento delle dimensioni _(fino a una scala massima specificata)_.
  - *Blend out. Engage:* ... inizia a combinare più _(dopo essere stato inattivo più sottile)_.  

- **Ondweller ()**: informa lo script di _Blend_ che la notifica è stata esaminata in modo sufficientemente appropriato.

- **OnLookAway ()**: la notifica inizia con...
  - *FaceUser. Disengage:* ... tornare all'orientamento originale.
  - *ChangeSize. Disengage:* ... Riduci le dimensioni originali.
  - *Blend out. Disengage:* ... inizia a Blend out: se è stato attivato _ondweller ()_ , Blend out completamente e distruggi; in caso contrario, torna allo stato inattivo.

**Considerazioni sulla progettazione:** La chiave per una piacevole esperienza consiste nell'ottimizzare con attenzione la velocità di uno di questi comportamenti, in modo da evitare la causa del disagio rispondendo troppo rapidamente al punto di vista dell'utente.
In caso contrario, questa operazione può essere estremamente travolgente.

<img src="../../Documentation/Images/EyeTracking/mrtk_et_EyeTrackingTarget_Notification.jpg" width="750" alt="MRTK target Notification">

### <a name="example-2-holographic-gem-rotates-slowly-when-looking-at-it"></a>Esempio #2: la gemma olografica ruota lentamente durante la ricerca

Analogamente a #1 di esempio, è possibile creare facilmente un feedback del passaggio del mouse per le gemme olografiche in una `EyeTrackingDemo-02-TargetSelection` scena (assets/MRTK/examples/Demos/eyetracking/scenes) che verrà ruotata lentamente in una direzione costante e a una velocità costante (contrariamente all'esempio di rotazione precedente) quando viene esaminato. È sufficiente attivare la rotazione della gemma olografica dall'evento _WhileLookingAtTarget ()_ di _EyeTrackingTarget_. Ecco alcuni dettagli:

1. Creare uno script generico che includa una funzione pubblica per ruotare il GameObject a cui è collegato. Di seguito è riportato un esempio di _RotateWithConstSpeedDir. cs_ in cui è possibile modificare la direzione e la velocità di rotazione dall'editor di Unity.

    ```c#
    using UnityEngine;

    namespace Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking
    {
        /// <summary>
        /// The associated GameObject will rotate when RotateTarget() is called based on a given direction and speed.
        /// </summary>
        public class RotateWithConstSpeedDir : MonoBehaviour
        {
            [Tooltip("Euler angles by which the object should be rotated by.")]
            [SerializeField]
            private Vector3 RotateByEulerAngles = Vector3.zero;

            [Tooltip("Rotation speed factor.")]
            [SerializeField]
            private float speed = 1f;

            /// <summary>
            /// Rotate game object based on specified rotation speed and Euler angles.
            /// </summary>
            public void RotateTarget()
            {
                transform.eulerAngles = transform.eulerAngles + RotateByEulerAngles * speed;
            }
        }
    }
    ```

1. Aggiungere lo [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script alla GameObject di destinazione e fare riferimento alla funzione _RotateTarget ()_ nel trigger UnityEvent, come illustrato nella schermata seguente:

    ![Esempio EyeTrackingTarget](../Images/EyeTracking/mrtk_et_EyeTrackingTargetSample.jpg)

### <a name="example-3-pop-those-gems-aka-_multi-modal-eye-gaze-supported-target-selection_"></a>Esempio di #3: pop The Gems aka _multimodale Eye-sguardi-supported target selection_

Nell'esempio precedente è stato illustrato quanto sia facile rilevare se una destinazione viene esaminata e come attivare una reazione. A questo punto, fare in modo che le gemme esplodano usando l'evento _OnSelected ()_ da [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) . La parte interessante è la *modalità* di attivazione della selezione. [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget)Consente di assegnare rapidamente diversi modi per richiamare una selezione:

- _Gesto del pizzico_: l'impostazione dell'azione ' Select ' su' Select ' usa il gesto della mano predefinito per attivare la selezione.
Ciò significa che l'utente può semplicemente alzare la mano e pizzicare il pollice e l'indice insieme per confermare la selezione.

- Pronunciare _"Select"_: usare il comando Voice predefinito _"Select"_ per selezionare un ologramma.

- Pronunciare " _Esplodi"_ o _"pop"_: per usare i comandi vocali personalizzati, è necessario eseguire due passaggi:
    1. Configurare un'azione personalizzata, ad esempio _"DestroyTarget"_
        - Passare a _MRTK-> input-> azioni di input_
        - Fare clic su "Aggiungi una nuova azione"

    2. Configurare i comandi vocali che attivano questa azione, ad esempio _"Esplodi"_ o _"pop"_
        - Passare a _MRTK-> input-> Speech_
        - Fare clic su "Aggiungi un nuovo comando vocale"
            - Associare l'azione appena creata
            - Assegnare un _KeyCode_ per consentire l'attivazione dell'azione tramite un pulsante premere

![Esempio di EyeTrackingTarget comandi vocali](../Images/EyeTracking/mrtk_et_voicecmdsample.jpg)

Quando si seleziona una gemma, l'operazione verrà esplosa, rendendo un suono e scomparirà. Questa operazione viene gestita dallo [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) script. Sono disponibili due opzioni:

- **Nell'editor di Unity:** È sufficiente collegare lo script associato a ognuno dei modelli Gem all'evento OnSelected () Unity nell'editor di Unity.
- **Nel codice:** Se non si desidera trascinare GameObject in questo modo, è anche possibile aggiungere semplicemente un listener di eventi direttamente allo script.  
Di seguito è riportato un esempio di come è stato fatto nello [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) script:

```c#
/// <summary>
/// Destroys the game object when selected and optionally plays a sound or animation when destroyed.
/// </summary>
[RequireComponent(typeof(EyeTrackingTarget))] // This helps to ensure that the EyeTrackingTarget is attached
public class HitBehaviorDestroyOnSelect : MonoBehaviour
{
    ...
    private EyeTrackingTarget myEyeTrackingTarget = null;

    private void Start()
    {
        myEyeTrackingTarget = this.GetComponent<EyeTrackingTarget>();

        if (myEyeTrackingTarget != null)
        {
            myEyeTrackingTarget.OnSelected.AddListener(TargetSelected);
        }
    }

    ...

    ///
    /// This is called once the EyeTrackingTarget detected a selection.
    ///
    public void TargetSelected()
    {
        // Play some animation
        // Play some audio effect
        // Handle destroying the target appropriately
    }
}
```

### <a name="example-4-use-hand-rays-and-eye-gaze-input-together"></a>Esempio di #4: usare i raggi mano e l'input dello sguardo oculare insieme

I raggi di mano hanno la priorità rispetto alla destinazione e agli sguardi oculari. Ciò significa che, se sono abilitati i raggi mano, il momento in cui vengono visualizzate le lancette, il raggio della mano fungerà da puntatore primario.
Tuttavia, potrebbero esserci situazioni in cui si desidera utilizzare i raggi mano, pur continuando a rilevare se un utente sta osservando un certo ologramma. Facile! Essenzialmente sono necessari due passaggi:

**1. abilitare il raggio della mano:** per abilitare il raggio della mano, passare a _mixed reality Toolkit-> puntatori di input->_.
In _EyeTrackingDemo-00-RootScene_ , in cui il Toolkit di realtà misto viene configurato una sola volta per tutte le scene demo di rilevamento degli occhi, viene visualizzato il _EyeTrackingDemoPointerProfile_.
È possibile creare un nuovo _profilo di input_ da zero o adattare il rilevamento degli occhi corrente:

- **Da zero:** Nella scheda _puntatori_ selezionare _DefaultMixedRealityInputPointerProfile_ dal menu di scelta rapida.
Si tratta del profilo puntatore predefinito per il quale è già abilitato il raggio di mano.
Per modificare il cursore predefinito (un punto bianco opaco), è sufficiente clonare il profilo e creare un profilo puntatore personalizzato.
Sostituire quindi _DefaultCursor_ con _EyeGazeCursor_ sotto precostruzione del _cursore dello sguardo_.  
- **In base alla _EyeTrackingDemoPointerProfile_ esistente:** fare doppio clic su _EyeTrackingDemoPointerProfile_ e aggiungere la voce seguente in _Opzioni puntatore_:
  - **Tipo di controller:** ' Articolato a mano ',' realtà mista di Windows '
  - **Manualità:** Qualsiasi
  - **Prefabbricato puntatore:** DefaultControllerPointer

**2. rilevare l'aspetto di un ologramma:** usare lo [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script per abilitare il rilevamento di un ologramma come descritto in precedenza. È anche possibile esaminare lo `FollowEyeGaze` script di esempio per l'ispirazione perché mostra un ologramma che segue il proprio sguardo (ad esempio, un cursore) se i raggi di mano sono abilitati o meno.

A questo punto, quando si avviano le scene demo per la registrazione degli occhi, dovrebbe venire visualizzato un raggio dalle mani.
Ad esempio, nella demo di selezione della destinazione di rilevamento degli occhi, il cerchio semitrasparente continua a osservare il proprio sguardo e le gemme rispondono a se sono state esaminate o meno, mentre i pulsanti del menu della scena principale usano invece il puntatore di input primario (le mani).

---
[Torna a "Eye Tracking in the MixedRealityToolkit"](EyeTracking_Main.md)
