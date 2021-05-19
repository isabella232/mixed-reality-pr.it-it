---
title: Selezione del target di tracciamento oculare
description: Come accedere ai dati dello sguardo fisso e agli eventi specifici dello sguardo fisso per selezionare le destinazioni in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK, EyeTracking,
ms.openlocfilehash: 229903e01c597aefbb3fc29de8a49d79cbbd42d0
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144197"
---
# <a name="eye-supported-target-selection"></a>Selezione della destinazione supportata dagli occhi

![MRTK](../../images/eye-tracking/mrtk_et_targetselect.png)

Questa pagina illustra diverse opzioni per l'accesso ai dati dello sguardo fisso e a eventi specifici dello sguardo fisso per selezionare le destinazioni in MRTK. Il tracciamento oculare consente selezioni di destinazione veloci e senza sforzo usando una combinazione di informazioni su ciò che un utente sta esaminando con input aggiuntivi come il rilevamento manuale e i _comandi vocali:_ 

- Cercare & say _"Select"_ (comando vocale predefinito)
- Cercare & _"Explode"_ o _"Pop"_ (comandi vocali personalizzati)
- Cercare & Bluetooth
- Cercare & avvicinamento delle dita (ad esempio, tenere la mano davanti a te e avvicinare il pollice e l'indice)
  - Si noti che per il funzionamento, i [raggi della mano devono essere disabilitati](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray)

Per selezionare il contenuto olografico usando lo sguardo fisso, sono disponibili diverse opzioni:

[**1. Usare il puntatore dello stato attivo primario:**](#1-use-generic-focus-and-pointer-handlers)

Questo può essere inteso come cursore con priorità.
Per impostazione predefinita, se le mani sono visualizzate, si tratta di raggi della mano.
Se non sono presenti mani, il puntatore con priorità sarà la testa o lo sguardo fisso.
Di conseguenza, si noti che in base alla testa o lo sguardo oculare corrente viene eliminato come input del cursore se vengono usati i raggi della mano.

Esempio:

Un utente vuole selezionare un pulsante olografico distante.
Gli sviluppatori vogliono fornire una soluzione flessibile che consenta all'utente di eseguire queste attività in diverse condizioni:

- Accedere al pulsante e fare clic su di esso
- Guardarlo da una distanza e pronunciare "select"
- Imposta come destinazione il pulsante usando un raggio della mano ed eseguendo un avvicinamento delle dita. In questo caso, la soluzione più flessibile consiste nell'usare il gestore dello stato attivo principale, in quanto invierà una notifica ogni volta che il puntatore dello stato attivo primario attualmente in ordine di priorità attiva un evento. Si noti che se i raggi della mano sono abilitati, il puntatore di messa a fuoco con la testa o lo sguardo fisso viene disabilitato non appena le mani vengono visualizzate.

> [!IMPORTANT]
> Si noti che se i raggi della mano sono abilitati, il puntatore di messa a fuoco della testa o dello sguardo fisso viene disabilitato non appena le mani vengono visualizzate. Se si vuole supportare [ _un'interazione "look and pinch",_ è necessario disabilitare il raggio della mano.](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray) Nelle scene di esempio del tracciamento oculare il raggio della mano è stato disabilitato per consentire interazioni più complesse con occhi e movimenti della mano. Vedere ad esempio Posizionamento supportato dagli [occhi.](eye-tracking-eyes-and-hands.md)

[**2. Usare contemporaneamente sia la messa a fuoco oculare che i raggi della mano:**](#2-independent-eye-gaze-specific-eyetrackingtarget)

In alcuni casi può essere necessario essere più specifici del tipo di puntatore allo stato attivo che può attivare determinati eventi e consentire l'uso simultaneo di più tecniche di interazione da lontano.

Ad esempio: nell'app un utente può usare raggi della mano da lontano per manipolare alcune configurazioni meccaniche olografiche, ad esempio afferrare e tenere premute alcune parti del motore olografiche distanti e posizionarle sul posto. Durante questa operazione, l'utente deve eseguire una serie di istruzioni e registrare lo stato di avanzamento contrassegnando alcune caselle di controllo. Se l'utente ha le mani non occupate, sarebbe istintivo toccare semplicemente la casella di controllo o selezionarla usando un raggio della mano. Tuttavia, se l'utente ha le sue mani occupate, come nel nostro caso, tenendo presenti alcune parti del motore olografico, vuoi consentire all'utente di scorrere facilmente le istruzioni usando lo sguardo fisso e semplicemente guardare una casella di controllo e pronunciare "check it!".

Per abilitare questa funzionalità, è necessario usare lo script EyeTrackingTarget specifico dell'occhio, indipendente dai FocusHandler di MRTK di base e che verrà illustrato più avanti.

## <a name="1-use-generic-focus-and-pointer-handlers"></a>1. Usare gestori generici dello stato attivo e del puntatore

Se il tracciamento oculare è configurato correttamente (vedere Configurazione [MRTK](eye-tracking-basic-setup.md)di base per l'uso del tracciamento oculare), consentire agli utenti di selezionare ologrammi usando gli occhi è lo stesso di qualsiasi altro input di messa a fuoco (ad esempio, sguardo alla testa o raggio della mano). Ciò offre il grande vantaggio di un modo flessibile per interagire con gli ologrammi definendo il tipo di stato attivo principale nel profilo puntatore di input MRTK a seconda delle esigenze dell'utente, lasciando invariato il codice. Ciò consente di passare da uno sguardo alla testa o dall'altro senza modificare una riga di codice o sostituire i raggi della mano con il targeting oculare per le interazioni lontano.

### <a name="focusing-on-a-hologram"></a>Concentrarsi su un ologramma

Per rilevare quando un ologramma è attivo, usare _l'interfaccia 'IMixedRealityFocusHandler'_ che fornisce due membri di interfaccia: _OnFocusEnter_ e _OnFocusExit_.

Ecco un semplice esempio di [ColorTap.cs](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ColorTap) per modificare il colore di un ologramma quando viene esaminato.

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

### <a name="selecting-a-focused-hologram"></a>Selezione di un ologramma con stato attivo

Per selezionare un ologramma con stato attivo, usare _PointerHandler_ per restare in ascolto degli eventi di input per confermare una selezione.
Ad esempio, l'aggiunta _di IMixedRealityPointerHandler_ li farà reagire all'input del puntatore semplice.
_L'interfaccia IMixedRealityPointerHandler_ richiede l'implementazione dei tre membri di interfaccia _seguenti: OnPointerUp_, _OnPointerDown_ e _OnPointerClicked_.

Nell'esempio seguente viene modificato il colore di un ologramma osservandolo e avvicinando o pronunciando "select".
L'azione necessaria per attivare l'evento è definita da in base alla quale è possibile impostare il tipo di nell'editor di Unity. Per impostazione predefinita, si tratta `eventData.MixedRealityInputAction == selectAction` `selectAction` dell'azione "Seleziona". I tipi di [MixedRealityInputActions](../input-actions.md) disponibili possono essere configurati nel profilo MRTK tramite azioni di input del profilo di configurazione _MRTK._  ->    ->  

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

### <a name="eye-gaze-specific-baseeyefocushandler"></a>BaseEyeFocusHandler specifico dello sguardo fisso

Dato che lo sguardo oculare può essere molto diverso da altri input del puntatore,  è possibile assicurarsi di reagire all'input dello stato attivo solo se è lo sguardo fisso e attualmente è il puntatore di input primario.
A questo scopo, si userebbe l'oggetto specifico per il tracciamento [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) oculare e che deriva da [`BaseFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseFocusHandler) .
Come accennato in precedenza, verrà attivato solo se il targeting dello sguardo fisso è attualmente l'input del puntatore primario (ad esempio, non è attivo alcun raggio della mano). Per altre informazioni, vedere Come supportare lo sguardo [fisso e i movimenti della mano.](eye-tracking-eyes-and-hands.md)

Ecco un esempio da `EyeTrackingDemo-03-Navigation` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes).
In questa demo sono presenti due ologrammi 3D che si attivano a seconda della parte dell'oggetto da guardare: se l'utente osserva il lato sinistro dell'ologramma, tale parte si sposterà lentamente verso la parte anteriore rivolta verso l'utente.
Se viene esaminato il lato destro, tale parte si sposterà lentamente verso la parte anteriore.
Si tratta di un comportamento che potrebbe non essere attivo in qualsiasi momento e anche qualcosa che potrebbe non essere necessario attivare accidentalmente con un raggio della mano o uno sguardo alla testa.
Dopo [`OnLookAtRotateByEyeGaze`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.OnLookAtRotateByEyeGaze) l'associazione, un GameObject verrà ruotato mentre viene esaminato.

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

- **OnEyeFocusStart:** Attivato quando il raggio dello sguardo visivo *inizia* a intersecarsi con il collisore di questo obiettivo.
- **OnEyeFocusStay:** Attivato mentre *il* raggio dello sguardo oculare si interseca con il collisore di questo obiettivo.
- **OnEyeFocusStop:** Attivato quando il raggio dello sguardo *fisso smette* di intersecarsi con il collisore di questo obiettivo.
- **OnEyeFocusDwell:** Attivato dopo che il raggio dello sguardo oculare si è intersecato con il collisore di questo obiettivo per un periodo di tempo specificato.

## <a name="2-independent-eye-gaze-specific-eyetrackingtarget"></a>2. EyeTrackingTarget indipendente specifico dello sguardo visivo

Infine, è possibile offrire una soluzione che consente di trattare l'input basato sugli occhi completamente indipendente dagli altri puntatori dello stato attivo tramite lo [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script.

Ciò offre tre _vantaggi:_

- È possibile assicurarsi che l'ologramma reagisca solo con lo sguardo dell'utente.
- È indipendente dall'input primario attualmente attivo. Di conseguenza, è possibile elaborare più input contemporaneamente, ad esempio combinando il targeting oculare veloce con i movimenti della mano.
- Diversi eventi di Unity sono già stati impostati per rendere più veloce e pratico gestire e riutilizzare i comportamenti esistenti dall'interno dell'editor di Unity o tramite codice.

Esistono anche _alcuni svantaggi:_

- Maggiore impegno nella gestione di input separati singolarmente.
- Nessuna degradazione elegante: supporta solo il targeting oculare. Se il tracciamento oculare non funziona, è necessario un fallback aggiuntivo.

Analogamente a _BaseFocusHandler,_ _EyeTrackingTarget_ è pronto con diversi eventi Unity specifici dello sguardo fisso che è possibile ascoltare facilmente tramite l'editor di Unity (vedere l'esempio seguente) o usando _AddListener()_ nel codice:

- OnLookAtStart()
- WhileLookingAtTarget()
- OnLookAway()
- OnDwell()
- OnSelected()

Di seguito vengono illustrati alcuni esempi di come usare _EyeTrackingTarget._

### <a name="example-1-eye-supported-smart-notifications"></a>Esempio #1: Notifiche intelligenti supportate dagli occhi

In `EyeTrackingDemo-02-TargetSelection` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes) è possibile trovare un esempio di _notifiche_ intelligenti che reagiscono al sguardo fisso.
Si tratta di caselle di testo 3D che possono essere posizionate nella scena e che vengono ingrandite e ruotate in modo uniforme verso l'utente quando viene esaminato per semplificare la leggibilità. Mentre l'utente legge la notifica, le informazioni continuano a essere visualizzate chiare e chiare. Dopo la lettura e l'allontanarsi dalla notifica, la notifica verrà automaticamente ignorata e si dissolverà. A tale scopo, esistono alcuni script di comportamento generici che non sono specifici del tracciamento oculare, ad esempio:

- [`FaceUser`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FaceUser)
- [`ChangeSize`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ChangeSize)
- [`BlendOut`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.BlendOut)

Il vantaggio di questo approccio è che gli stessi script possono essere riutilizzati da vari eventi. Ad esempio, un ologramma può iniziare ad affrontare l'utente in base a comandi vocali o dopo aver premuto un pulsante virtuale. Per attivare questi eventi, è sufficiente fare riferimento ai metodi che devono essere eseguiti nello script associato [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) a GameObject.

Per l'esempio delle _"notifiche intelligenti e attente",_ si verifica quanto segue:

- **OnLookAtStart():** la notifica inizia a...
  - *FaceUser.Engage:* ... rivolgersi all'utente.
  - *ChangeSize.Engage:* ... aumento delle _dimensioni (fino a una scala massima specificata)_.
  - *BlendOut.Engage:* ... inizia a integrarsi in più _(dopo essere in uno stato di inattività più sottile)_.  

- **OnDwell():** informa lo script _BlendOut_ che la notifica è stata osservata sufficientemente.

- **OnLookAway():** la notifica inizia a...
  - *FaceUser.Disengage:* ... tornare all'orientamento originale.
  - *ChangeSize.Disengage:* ... tornare alle dimensioni originali.
  - *BlendOut.Disengage:* ... inizia a confondersi: se _OnDwell()_ è stato attivato, si fondono completamente ed eliminano, in caso contrario torna allo stato inattivo.

**Considerazioni sulla progettazione:** La chiave per un'esperienza piacevole è ottimizzare con attenzione la velocità di uno di questi comportamenti per evitare di causare disagio reagendo troppo rapidamente all'occhio dell'utente.
In caso contrario, può essere estremamente difficile.

<img src="../../images/eye-tracking/mrtk_et_EyeTrackingTarget_Notification.jpg" width="750" alt="Target Notification">

### <a name="example-2-holographic-gem-rotates-slowly-when-looking-at-it"></a>Esempio #2: gemma olografica ruota lentamente quando la si guarda

Analogamente a Example #1, è possibile creare facilmente un feedback al passaggio del mouse per le gemme olografiche nella scena (Assets/MRTK/Examples/Demos/EyeTracking/Scenes) che ruota lentamente in una direzione costante e a una velocità costante (a differenza dell'esempio di rotazione dall'alto) quando viene `EyeTrackingDemo-02-TargetSelection` esaminato. È necessario attivare la rotazione della gemma olografica dall'evento _WhileLookingAtTarget()_ di _EyeTrackingTarget._ Ecco alcuni altri dettagli:

1. Creare uno script generico che includa una funzione pubblica per ruotare l'oggetto GameObject a cui è collegata. Di seguito è riportato un esempio _di RotateWithConstSpeedDir.cs_ in cui è possibile modificare la direzione di rotazione e la velocità dall'editor di Unity.

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

1. Aggiungere lo script al GameObject di destinazione [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) e fare riferimento alla funzione _RotateTarget()_ nel trigger UnityEvent, come illustrato nello screenshot seguente:

    ![Esempio di EyeTrackingTarget](../../images/eye-tracking/mrtk_et_EyeTrackingTargetSample.jpg)

### <a name="example-3-pop-those-gems-aka-_multi-modal-eye-gaze-supported-target-selection_"></a>Esempio #3: Selezionare le gemme come selezione di destinazione _multimodale supportata_ da sguardo fisso

Nell'esempio precedente è stato illustrato quanto sia facile rilevare se una destinazione viene osservata e come attivare una reazione a tale obiettivo. Ora le gemme esplodono usando _l'evento OnSelected()_ di [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) . La parte interessante è *il modo* in cui viene attivata la selezione. consente [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) di assegnare rapidamente diversi modi per richiamare una selezione:

- _Movimento di avvicinamento_ delle dita: l'impostazione di "Seleziona azione" su "Seleziona" usa il movimento della mano predefinito per attivare la selezione.
Ciò significa che l'utente può semplicemente alzare la mano e avvicinare il pollice e il dito indice per confermare la selezione.

- Pronunciare _"Seleziona":_ usare il comando vocale _predefinito "Seleziona"_ per selezionare un ologramma.

- Pronunciare _"Explode"_ _o "Pop":_ per usare comandi vocali personalizzati, è necessario seguire due passaggi:
    1. Configurare un'azione personalizzata, ad esempio _"DestroyTarget"_
        - Passare a _MRTK -> Input -> Input Actions_
        - Fare clic su "Aggiungi una nuova azione"

    2. Configurare i comandi vocali che attivano questa azione, ad esempio _"Explode"_ o _"Pop"_
        - Passare a _MRTK -> Input -> Voce_
        - Fare clic su "Aggiungi un nuovo comando vocale"
            - Associare l'azione appena creata
            - Assegnare _un keycode_ per consentire l'attivazione dell'azione tramite la pressione di un pulsante

![Esempio di EyeTrackingTarget per i comandi vocali](../../images/eye-tracking/mrtk_et_voicecmdsample.jpg)

Quando viene selezionata una gemma, esplode, facendo un suono e scomparendo. Questa operazione viene gestita dallo [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) script. Sono disponibili due opzioni:

- **Nell'editor di Unity:** È possibile collegare semplicemente lo script collegato a ognuno dei modelli di gemme all'evento Unity OnSelected() nell'editor di Unity.
- **Nel codice:** Se non si vuole trascinare e rilasciare GameObject, è anche possibile aggiungere semplicemente un listener di eventi direttamente allo script.  
Di seguito è riportato un esempio di come è stato eseguito nello [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) script:

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

### <a name="example-4-use-hand-rays-and-eye-gaze-input-together"></a>Esempio #4: Usare i raggi della mano e l'input dello sguardo fisso insieme

I raggi della mano hanno la priorità rispetto alla destinazione della testa e dello sguardo fisso. Ciò significa che, se i raggi della mano sono abilitati, nel momento in cui le mani vengono visualizzate, il raggio della mano fungerà da indicatore di misura principale.
Tuttavia, in alcune situazioni potrebbe essere necessario usare i raggi della mano pur continuando a rilevare se un utente sta esaminando un determinato ologramma. Facile! In sostanza sono necessari due passaggi:

**1. Abilitare il raggio** della mano: per abilitare il raggio della mano, passare a Mixed Reality Toolkit _-> Input -> Pointers (Puntatori di input -> realtà mista)._
In _EyeTrackingDemo-00-RootScene,_ in cui Mixed Reality Toolkit è configurato una sola volta per tutte le scene demo di tracciamento oculare, dovrebbe essere visualizzato _EyeTrackingDemoPointerProfile._
È possibile creare un nuovo profilo _di input_ da zero o adattare il tracciamento oculare corrente:

- **Da zero:** Nella scheda _Puntatori_ selezionare _DefaultMixedRealityInputPointerProfile_ dal menu di scelta rapida.
Questo è il profilo puntatore predefinito in cui è già abilitato il raggio della mano.
Per modificare il cursore predefinito (un punto bianco opaco), è sufficiente clonare il profilo e creare un profilo puntatore personalizzato.
Sostituire quindi _DefaultCursor con_ _EyeGazeCursor_ in _Gaze Cursor Prefab (Prefab cursore sguardo fisso)._  
- **In base all'elemento _EyeTrackingDemoPointerProfile_ esistente:** fare doppio clic su _EyeTrackingDemoPointerProfile_ e aggiungere la voce seguente in _Pointer Options (Opzioni puntatore):_
  - **Tipo di controller:** 'Articulated Hand', 'Windows Mixed Reality'
  - **Mania:** Qualsiasi
  - **Prefab puntatore:** DefaultControllerPointer

**2. Rilevare che un ologramma** viene esaminato: usare lo script per abilitare il rilevamento che un ologramma viene esaminato [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) come descritto in precedenza. È anche possibile esaminare lo script di esempio per trovare ispirazione, in quanto mostra un ologramma che segue lo sguardo (ad esempio, un cursore) indipendentemente dal fatto che i raggi della mano siano abilitati o `FollowEyeGaze` meno.

Ora, quando si avviano le scene della demo di tracciamento oculare, si dovrebbe vedere un raggio proveniente dalle mani.
Ad esempio, nella demo di selezione della destinazione del tracciamento oculare, il cerchio semitrasparente sta ancora seguendo lo sguardo e le gemme rispondono se vengono osservate o meno, mentre i pulsanti del menu della scena superiore usano invece il puntatore di input primario (le mani).

---
[Tornare a "Tracciamento oculare in MixedRealityToolkit"](eye-tracking-main.md)
