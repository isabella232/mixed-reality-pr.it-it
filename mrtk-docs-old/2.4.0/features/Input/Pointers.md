---
title: Pointers
description: Documentazione sui puntatori in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, puntatori,
ms.openlocfilehash: badf1caa2506dac9eae01e1f371efd461e085696
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783150"
---
# <a name="pointers"></a>Pointers

![Puntatore](../Images/Pointers/MRTK_Pointer_Main.png)

Questo articolo illustra come configurare e rispondere all'input del puntatore in pratica rispetto all' [architettura del puntatore](../../architecture/InputSystem/ControllersPointersAndFocus.md)

I puntatori vengono automaticamente istanze in fase di esecuzione quando viene rilevato un nuovo controller. È possibile collegare più di un puntatore a un controller. Con il profilo puntatore predefinito, ad esempio, i controller di realtà mista di Windows ottengono rispettivamente una linea e un puntatore parabolico per la selezione e la teleportazione normali.

## <a name="pointer-configuration"></a>Configurazione puntatore

I puntatori sono configurati come parte del sistema di input in MRTK tramite un [`MixedRealityPointerProfile`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile) . Questo tipo di profilo viene assegnato a un oggetto [`MixedRealityInputSystemProfile`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSystemProfile) in controllo configurazione MRTK. Il profilo del puntatore determina il cursore, i tipi di puntatori disponibili in fase di esecuzione e il modo in cui tali puntatori comunicano tra loro per decidere quale sia attivo.

- *Extent di puntamento* : definisce la distanza massima per cui un puntatore può interagire con un GameObject.

- *Pointing Raycast layer masks* : si tratta di una matrice con priorità di LayerMasks per determinare quali possibili GameObject qualsiasi puntatore specificato possono interagire con e l'ordine di interazione da tentare. Questo può essere utile per garantire che i puntatori interagiscano con gli elementi dell'interfaccia utente prima di altri oggetti della scena.
![Esempio di profilo puntatore](../Images/Input/Pointers/PointerProfile.PNG)

### <a name="pointer-options-configuration"></a>Configurazione delle opzioni del puntatore

La configurazione predefinita del profilo puntatore MRTK include le classi di puntatore seguenti e i prefabbricati associati. L'elenco di puntatori disponibili per il sistema in fase di esecuzione è definito in *Opzioni puntatore* nel profilo puntatore. Gli sviluppatori possono utilizzare questo elenco per riconfigurare i puntatori esistenti, aggiungere nuovi puntatori o eliminarne uno.

![Esempio di profilo Opzioni puntatore](../Images/Input/Pointers/PointerOptionsProfile.PNG)

Ogni voce del puntatore viene definita dal set di dati seguente:

- *Tipo di controller* : il set di controller per cui è valido un puntatore.
  - Ad esempio, *PokePointer* è responsabile per gli oggetti "frugare" con un dito e è, per impostazione predefinita, contrassegnato come supporto solo per il tipo di controller a mano articolata. Viene creata un'istanza dei puntatori solo quando un controller diventa disponibile e in particolare il *tipo di controller* definisce quali controller possono essere creati da questo puntatore.

- *Manualità* : consente di creare un'istanza di un puntatore solo per una mano specifica (a sinistra o a destra)

> [!NOTE]
> Se si imposta la proprietà della *manualità* di una voce del puntatore su *None* , questa verrà disabilitata dal sistema come alternativa alla rimozione del puntatore dall'elenco.

- *Prefabbricato del puntatore* : verrà creata un'istanza dell'asset prefabbricato quando un controller che corrisponde al tipo di controller e alla manualità specificati inizierà a essere rilevato.

È possibile avere più puntatori associati a un controller. Ad esempio, in `DefaultHoloLens2InputSystemProfile` (assets/MRTK/SDK/Profiles/HoloLens2/) il controller a mano articolata è associato a *PokePointer*, *GrabPointer* e *DefaultControllerPointer* (ovvero raggi mano).

> [!NOTE]
> MRTK fornisce un set di prefabbricati puntatore in *assets/MRTK/SDK/features/UX/premises/puntatori*. Una nuova precostruzione personalizzata può essere compilata purché contenga uno degli script di puntatore in *assets/MRTK/SDK/features/UX/scripts/puntatori* o qualsiasi altro script che implementa [`IMixedRealityPointer`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointer) .

### <a name="default-pointer-classes"></a>Classi puntatore predefinite

Le classi seguenti sono i puntatori MRTK predefiniti disponibili e definiti nel *profilo puntatore MRTK* predefinito descritto in precedenza. Ogni prefabbricato del puntatore fornito in *assets/MRTK/SDK/features/UX/Prefabbricates/puntatori* contiene uno dei componenti del puntatore collegati.

![Puntatori predefiniti MRTK](../Images/Input/Pointers/MRTK_Pointers.png)

#### <a name="far-pointers"></a>Puntatori a distanza

##### [`LinePointer`](xref:Microsoft.MixedReality.Toolkit.Input.LinePointer)

 *LinePointer*, una classe puntatore di base, disegna una linea dall'origine dell'input (ovvero il controller) nella direzione del puntatore e supporta un solo cast a raggio in questa direzione. In genere, [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) viene creata un'istanza delle classi figlio come e i puntatori di Teleport, che consentono di indicare la posizione in cui si trova la teleporta, anziché questa classe, che fornisce principalmente funzionalità comuni.

Per i controller di movimento come in Oculus, vive e la realtà mista di Windows, la rotazione corrisponderà alla rotazione del controller. Per gli altri controller, ad esempio HoloLens 2, la rotazione corrisponde alla punta della mano fornita dal sistema.

<img src="../Images/Pointers/MRTK_Pointers_Line.png" width="400">

##### [`CurvePointer`](xref:Microsoft.MixedReality.Toolkit.Input.CurvePointer)

*CurvePointer* estende la classe *LinePointer* consentendo il cast dei raggi in più passaggi lungo una curva. Questa classe di puntatore di base è utile per le istanze curve, ad esempio i puntatori di teleportazione in cui la linea si piega in modo coerente in una parabola.

##### [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer)

L'implementazione di *ShellHandRayPointer*, che si estende da [`LinePointer`](xref:Microsoft.MixedReality.Toolkit.Input.MousePointer) , viene usata come impostazione predefinita per il *profilo del puntatore MRTK*. Il prefabbricato *DefaultControllerPointer* implementa la [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) classe.

##### [`GGVPointer`](xref:Microsoft.MixedReality.Toolkit.Input.GGVPointer)

Noto anche come puntatore a *sguardi/movimenti/voce (GGV)* , GGVPointer alimenta le interazioni di tipo "1" e "tocco", principalmente tramite lo sguardo e il tocco aereo o l'interazione con selezione voce. La posizione e la direzione del puntatore GGV sono determinate dalla posizione e dalla rotazione della testa.

##### [`TouchPointer`](xref:Microsoft.MixedReality.Toolkit.Input.TouchPointer)

Il *TouchPointer* è responsabile dell'uso di Unity touch input (ad esempio touchscreen). Si tratta di "Interactions", perché l'azione di toccare lo schermo consente di eseguire il cast di un raggio dalla fotocamera a una posizione potenzialmente lontana nella scena.

##### [`MousePointer`](xref:Microsoft.MixedReality.Toolkit.Input.MousePointer)

Il *MousePointer* alimenta una schermata per la Raycast globale per le interazioni di gran lunga, ma per il mouse anziché il tocco.

![Puntatore del mouse](../Images/Pointers/MRTK_MousePointer.png)

> [!NOTE]
> Il supporto del mouse non è disponibile per impostazione predefinita in MRTK, ma può essere abilitato aggiungendo un nuovo *provider di dati di input* di tipo [`MouseDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.MouseDeviceManager) al profilo di input MRTK e assegnando al [`MixedRealityMouseInputProfile`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityMouseInputProfile) provider di dati.

#### <a name="near-pointers"></a>Near puntatori

##### [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer)

*[PokePointer](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer)* viene usato per interagire con gli oggetti del gioco che supportano "near Interaction touchable". ovvero GameObject a cui è associato uno [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) script. Nel caso di UnityUI, questo puntatore Cerca NearInteractionTouchableUnityUIs.  PokePointer usa un SphereCast per determinare l'elemento ritoccabile più vicino e viene usato per potenziare elementi come i pulsanti stampabili.

 Quando si configura GameObject con il [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) componente, assicurarsi di configurare il parametro *localForward* in modo che punti all'inizio del pulsante o di un altro oggetto che deve essere reso toccabile. Assicurarsi inoltre che i *limiti* di touchable corrispondano ai limiti dell'oggetto toccabile.

Proprietà del puntatore poke utili:

- *TouchableDistance*: distanza massima in cui è possibile interagire con una superficie toccabile
- Oggetti *visivi*: oggetto gioco usato per eseguire il rendering dell'oggetto visivo della descrizione comando (l'anello sul dito, per impostazione predefinita).
- *Line*: linea facoltativa da trascinare da un dito alla superficie di input attiva.
- *Maschere livello poke* : matrice con priorità di LayerMasks per determinare il GameObject possibile con cui può interagire il puntatore e l'ordine di interazione da tentare. Si noti che un GameObject deve avere anche un `NearInteractionTouchable` componente per interagire con un puntatore poke.

<img src="../Images/Pointers/MRTK_PokePointer.png" width="400">

##### [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer)

*[SpherePointer](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer)* utilizza [UnityEngine. Physics. OverlapSphere](https://docs.unity3d.com/ScriptReference/Physics.OverlapSphere.html) per identificare l'oggetto più vicino per l' [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) interazione, che risulta utile per l'input "afferrabile", ad esempio `ManipulationHandler` . Analogamente alla [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) / [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) coppia funzionale, per poter interagire con il puntatore a sfera, l'oggetto Game deve contenere un componente che rappresenta lo [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) script.

<img src="../Images/Pointers/MRTK_GrabPointer.jpg" width="400">

Proprietà del puntatore della sfera utili:

- *Raggio del cast della sfera*: raggio per la sfera utilizzata per eseguire una query per gli oggetti afferrabili.
- *Acquisisci maschere di livello* : una matrice con priorità di LayerMasks per determinare il GameObject possibile con cui può interagire il puntatore e l'ordine di interazione da tentare. Si noti che un GameObject deve avere anche un oggetto `NearInteractionGrabbable` per interagire con un SpherePointer.
    > [!NOTE]
    > Il livello di riconoscimento spaziale è disabilitato nel prefabbricato GrabPointer predefinito fornito da MRTK. Questa operazione viene eseguita per ridurre l'effetto sulle prestazioni dell'esecuzione di una query di sovrapposizione delle sfere con la mesh spaziale. Questa operazione può essere abilitata modificando il prefabbricato GrabPointer.
- *Ignorare i conflitti non in FOV* -se ignorare i Collider che potrebbero essere vicini al puntatore, ma non effettivamente nell'oggetto visivo FOV.
Questa operazione può impedire le catture accidentali e consentirà di attivare i raggi mano quando si può trovarsi vicino a un oggetto afferrabile, ma non può essere visualizzato. L'oggetto *visivo FOV* viene definito tramite un cono anziché il tronco tipico per motivi di prestazioni. Questo cono è centrato e orientato allo stesso modo in cui si trova il tronco della fotocamera con un raggio uguale a metà di visualizzazione (o di FOV verticale).

<img src="../Images/Input/Pointers/SpherePointer_VisualFOV.png" width="200">

#### <a name="teleport-pointers"></a>Puntatori Teleport

- [`TeleportPointer`](xref:Microsoft.MixedReality.Toolkit.Teleport.TeleportPointer) genererà una richiesta di Teleport quando viene eseguita l'azione (ad esempio viene premuto il pulsante Teleport per spostare l'utente.
- [`ParabolicTeleportPointer`](xref:Microsoft.MixedReality.Toolkit.Teleport.ParabolicTeleportPointer) genererà una richiesta di Teleport quando viene eseguita l'azione (ad esempio il pulsante teleport viene premuto con una linea parabolica Raycast per spostare l'utente.

<img src="../Images/Pointers/MRTK_Pointers_Parabolic.png" width="400">

## <a name="pointer-support-for-mixed-reality-platforms"></a>Supporto del puntatore per le piattaforme di realtà miste

La tabella seguente illustra in dettaglio i tipi di puntatore che vengono in genere usati per le piattaforme comuni in MRTK. Nota: è possibile aggiungere diversi tipi di puntatore a queste piattaforme. Ad esempio, è possibile aggiungere un puntatore poke o un puntatore a sfera a VR. Inoltre, i dispositivi VR con un gamepad possono usare il puntatore GGV.

|                     | OpenVR  | Windows Mixed Reality | HoloLens 1 | HoloLens 2 |
|---------------------|---------|-----------------------|------------|------------|
| ShellHandRayPointer | Valido   | Valido                 |            | Valido      |
| TeleportPointer     | Valido   | Valido                 |            |            |
| GGVPointer          |         |                       | Valido      |            |
| SpherePointer       |         |                       |            | Valido      |
| PokePointer         |         |                       |            | Valido      |

## <a name="pointer-interactions-via-code"></a>Interazioni tra puntatori tramite codice

### <a name="pointer-event-interfaces"></a>Interfacce eventi puntatore

I monobehavior che implementano una o più delle interfacce seguenti e sono assegnati a un GameObject con un oggetto riceverà `Collider` gli eventi di interazione del puntatore come definito dall'interfaccia associata.

| Event | Descrizione | Gestore |
| --- | --- | --- |
| Prima dello stato attivo modificato/stato attivo modificato | Generato nell'oggetto Game che perde lo stato attivo e quello che lo ottiene ogni volta che un puntatore cambia lo stato attivo. | [`IMixedRealityFocusChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusChangedHandler) |
Invio/uscita dello stato attivo | Generato sull'oggetto gioco che ottiene lo stato attivo quando il primo puntatore lo immette e su quello che perde lo stato attivo quando l'ultimo puntatore lo lascia. | [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler)
Puntatore inattivo/trascinamento/clic | Elevato per segnalare la pressione, il trascinamento e il rilascio del puntatore. | [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler)
Tocco avviato/aggiornato/completato | Generato da puntatori compatibili con il tocco come [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) per segnalare l'attività di tocco. | [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)

> [!NOTE]
> [`IMixedRealityFocusChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusChangedHandler) e [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler) devono essere gestiti negli oggetti in cui vengono generati. È possibile ricevere eventi di attivazione a livello globale, ma, a differenza di altri eventi di input, il gestore eventi globale non blocca la ricezione degli eventi in base allo stato attivo (l'evento verrà ricevuto dal gestore globale e da un oggetto corrispondente nello stato attivo).

#### <a name="pointer-input-events-in-action"></a>Eventi di input puntatore in azione

Gli eventi di input del puntatore vengono riconosciuti e gestiti dal sistema di input MRTK in modo analogo [agli eventi di input normali](InputEvents.md#input-events-in-action). La differenza consiste nel fatto che gli eventi di input del puntatore vengono gestiti solo da GameObject nello stato attivo dal puntatore che ha attivato l'evento di input, nonché da eventuali gestori di input globali. Gli eventi di input normali vengono gestiti da GameObject in stato attivo per tutti i puntatori attivi.

1. Il sistema di input MRTK riconosce che si è verificato un evento di input
1. Il sistema di input MRTK genera la funzione di interfaccia pertinente per l'evento di input in tutti i gestori di input globali registrati
1. Il sistema di input determina quale GameObject è attivo per il puntatore che ha attivato l'evento
    1. Il sistema di input usa il [sistema di eventi di Unity](https://docs.unity3d.com/Manual/EventSystem.html) per attivare la funzione di interfaccia pertinente per tutti i componenti corrispondenti nel GameObject con stato attivo
    1. Se in qualsiasi momento un evento di input è stato [contrassegnato come usato](inputevents.md#how-to-stop-input-events), il processo terminerà e nessun altro GameObject riceverà i callback.
        - Esempio: ai componenti che implementano l'interfaccia [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) verrà eseguita la ricerca di un GameObject guadagni o perde lo stato attivo
        - Nota: il sistema di eventi Unity verrà propagato per eseguire una ricerca nel GameObject padre se non sono stati trovati componenti corrispondenti all'interfaccia desiderata nel GameObject corrente.
1. Se non viene registrato alcun gestore di input globale e non viene trovato alcun GameObject con un componente/interfaccia corrispondente, il sistema di input chiamerà ogni gestore di input registrato di fallback.

#### <a name="example"></a>Esempio

Di seguito è riportato uno script di esempio che modifica il colore del renderer collegato quando un puntatore accetta o lascia lo stato attivo o quando un puntatore seleziona l'oggetto.

```c#
public class ColorTap : MonoBehaviour, IMixedRealityFocusHandler, IMixedRealityPointerHandler
{
    private Color color_IdleState = Color.cyan;
    private Color color_OnHover = Color.white;
    private Color color_OnSelect = Color.blue;
    private Material material;

    private void Awake()
    {
        material = GetComponent<Renderer>().material;
    }

    void IMixedRealityFocusHandler.OnFocusEnter(FocusEventData eventData)
    {
        material.color = color_OnHover;
    }

    void IMixedRealityFocusHandler.OnFocusExit(FocusEventData eventData)
    {
        material.color = color_IdleState;
    }

    void IMixedRealityPointerHandler.OnPointerDown(
         MixedRealityPointerEventData eventData) { }

    void IMixedRealityPointerHandler.OnPointerDragged(
         MixedRealityPointerEventData eventData) { }

    void IMixedRealityPointerHandler.OnPointerClicked(MixedRealityPointerEventData eventData)
    {
        material.color = color_OnSelect;
    }
}
```

### <a name="query-pointers"></a>Puntatori di query

È possibile raccogliere tutti i puntatori attualmente attivi eseguendo un ciclo attraverso le origini di input disponibili, ad esempio controller e input disponibili) per individuare i puntatori a essi collegati.

```c#
var pointers = new HashSet<IMixedRealityPointer>();

// Find all valid pointers
foreach (var inputSource in CoreServices.InputSystem.DetectedInputSources)
{
    foreach (var pointer in inputSource.Pointers)
    {
        if (pointer.IsInteractionEnabled && !pointers.Contains(pointer))
        {
            pointers.Add(pointer);
        }
    }
}
```

#### <a name="primary-pointer"></a>Puntatore primario

Gli sviluppatori possono sottoscrivere l'evento PrimaryPointerChanged di FocusProviders per ricevere una notifica quando il puntatore primario è stato modificato. Questo può essere estremamente utile per identificare se l'utente sta attualmente interagendo con una scena tramite lo sguardo o un raggio di mano o un'altra origine di input.

```c#
private void OnEnable()
{
    var focusProvider = CoreServices.InputSystem?.FocusProvider;
    focusProvider?.SubscribeToPrimaryPointerChanged(OnPrimaryPointerChanged, true);
}

private void OnPrimaryPointerChanged(IMixedRealityPointer oldPointer, IMixedRealityPointer newPointer)
{
    ...
}

private void OnDisable()
{
    var focusProvider = CoreServices.InputSystem?.FocusProvider;
    focusProvider?.UnsubscribeFromPrimaryPointerChanged(OnPrimaryPointerChanged);

    // This flushes out the current primary pointer
    OnPrimaryPointerChanged(null, null);
}
```

La `PrimaryPointerExample` scena (assets/MRTK/examples/Demos/input/Scenes/PrimaryPointer) Mostra come usare la [`PrimaryPointerChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.PrimaryPointerChangedHandler) per gli eventi per rispondere a un nuovo puntatore primario.

<img src="../../Documentation/Images/Pointers/PrimaryPointerExample.png" style="max-width:100%;">

### <a name="pointer-result"></a>Risultato indicatore di misura

La [`Result`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointer.Result) Proprietà Pointer contiene il risultato corrente per la query della scena utilizzata per determinare l'oggetto con lo stato attivo. Per un puntatore Raycast, come quello creato per impostazione predefinita per i controller di movimento, l'input dello sguardo e il raggio della mano, conterrà la posizione e la normale della hit raycast.

```c#
private void IMixedRealityPointerHandler.OnPointerClicked(MixedRealityPointerEventData eventData)
{
    var result = eventData.Pointer.Result;
    var spawnPosition = result.Details.Point;
    var spawnRotation = Quaternion.LookRotation(result.Details.Normal);
    Instantiate(MyPrefab, spawnPosition, spawnRotation);
}
```

La `PointerResultExample` scena (assets/MRTK/examples/Demos/input/Scenes/PointerResult/PointerResultExample. Unity) Mostra come usare il puntatore [`Result`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointer.Result) per generare un oggetto in corrispondenza della posizione di hit.

<img src="../../Documentation/Images/Input/PointerResultExample.png" style="max-width:100%;">

### <a name="disable-pointers"></a>Disabilitare i puntatori

Per attivare e disattivare i puntatori, ad esempio per disabilitare il raggio della mano, impostare [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) per un tipo di puntatore specificato tramite [`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) .

```c#
// Disable the hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff);

// Disable hand rays for the right hand only
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Right);

// Disable the gaze pointer
PointerUtils.SetGazePointerBehavior(PointerBehavior.AlwaysOff);

// Set the behavior to match HoloLens 1
// Note, if on HoloLens 2, you must configure your pointer profile to make the GGV pointer show up for articulated hands.
public void SetHoloLens1()
{
    PointerUtils.SetPokePointerBehavior(PointerBehavior.AlwaysOff, Handedness.Any);
    PointerUtils.SetGrabPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Any);
    PointerUtils.SetRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Any);
    PointerUtils.SetGGVBehavior(PointerBehavior.Default);
}
```

[`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) Per altri esempi, vedere e.

## <a name="pointer-interactions-via-editor"></a>Interazioni tra puntatori tramite Editor

Per gli eventi del puntatore gestiti da [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) , MRTK offre ulteriore praticità sotto forma di [`PointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.PointerHandler) componente, che consente di gestire gli eventi del puntatore direttamente tramite gli eventi di Unity.

<img src="../Images/Pointers/PointerHandler.png" style="max-width:100%;">

## <a name="pointer-extent"></a>Extent del puntatore

I puntatori a distanza presentano impostazioni che limitano il modo in cui verranno Raycast e interagiranno con altri oggetti nella scena.
Per impostazione predefinita, questo valore è impostato su 10 metri. Questo valore è stato scelto per restare coerente con il comportamento della shell HoloLens.

Questo può essere modificato aggiornando i `DefaultControllerPointer` campi del componente del prefabbricato [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) :

*Extent del puntatore* : consente di controllare la distanza massima con cui i puntatori interagiranno.

*Extent del puntatore predefinito* : controlla la lunghezza del raggio/linea del puntatore che verrà eseguito quando il puntatore non interagisce con alcun elemento.

## <a name="see-also"></a>Vedi anche

- [Architettura del puntatore](../Architecture/InputSystem/ControllersPointersAndFocus.md)
- [Eventi di input](InputEvents.md)
