---
title: Pointers
description: Documentazione sui puntatori in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, puntatori,
ms.openlocfilehash: 9fec02e7866aaf867c7145491bfd84f727e039cdd7a4323ace9c65f74e49480a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115191753"
---
# <a name="pointers"></a>Pointers

![Puntatore](../images/pointers/MRTK_Pointer_Main.png)

Questo articolo illustra come configurare e rispondere all'input del puntatore in pratica, rispetto all'architettura [del puntatore](../../architecture/controllers-pointers-and-focus.md)

Le istanze dei puntatori vengono automaticamente inizializzate in fase di esecuzione quando viene rilevato un nuovo controller. È possibile collegare più puntatori a un controller. Ad esempio, con il profilo puntatore predefinito, i controller Windows Mixed Reality ottengono rispettivamente una linea e un indicatore di misura parabolico per la selezione normale e il teletrasporto.

## <a name="pointer-configuration"></a>Configurazione del puntatore

I puntatori sono configurati come parte del sistema di input in MRTK tramite [`MixedRealityPointerProfile`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile) . Questo tipo di profilo viene assegnato a un [`MixedRealityInputSystemProfile`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSystemProfile) oggetto nel controllo della configurazione di MRTK. Il profilo Puntatore determina il cursore, i tipi di puntatori disponibili in fase di esecuzione e il modo in cui tali puntatori comunicano tra loro per decidere quale è attivo.

- *Extent di puntamento:* definisce la distanza massima per cui un puntatore può interagire con un GameObject.

- *Maschera di livello Raycast* di puntamento: si tratta di una matrice con priorità di LayerMasks per determinare i gameobject possibili con cui un determinato puntatore può interagire e l'ordine di interazione da provare. Ciò può essere utile per garantire che i puntatori interagiscano con gli elementi dell'interfaccia utente prima di altri oggetti della scena.
![Esempio di profilo puntatore](../images/input/pointers/PointerProfile.PNG)

### <a name="pointer-options-configuration"></a>Configurazione delle opzioni del puntatore

La configurazione predefinita di MRTK Pointer Profile include le classi puntatore seguenti e i prefab associati predefiniti. L'elenco dei puntatori disponibili per il sistema in fase di esecuzione è definito in *Pointer Options (Opzioni puntatore)* nel profilo Pointer (Puntatore). Gli sviluppatori possono usare questo elenco per riconfigurare i puntatori esistenti, aggiungerne di nuovi o eliminarli.

![Esempio di profilo Opzioni puntatore](../images/input/pointers/PointerOptionsProfile.PNG)

Ogni voce pointer è definita dal set di dati seguente:

- *Tipo di controller:* set di controller per cui è valido un puntatore.
  - Ad esempio, *Il PokePointer* è responsabile del "poking" degli oggetti con un dito ed è, per impostazione predefinita, contrassegnato come supporto solo del tipo di controller della mano articolato. Viene creata un'istanza dei puntatori solo  quando un controller diventa disponibile e in particolare il tipo di controller definisce i controller con cui è possibile creare questo prefab del puntatore.

- *Handness* : consente la creazione di un'istanza di un puntatore solo per una mano specifica (sinistra/destra)

> [!NOTE]
> *L'impostazione della proprietà Handedness* di una voce Pointer su *None* la disabilita in modo efficace dal sistema in alternativa alla rimozione di tale puntatore dall'elenco.

- *Prefab* puntatore: verrà creata un'istanza di questo asset prefab quando un controller corrispondente al tipo di controller specificato e il numero di mani inizia a essere monitorato.

È possibile avere più puntatori associati a un controller. Ad esempio, in `DefaultHoloLens2InputSystemProfile` (Assets/MRTK/SDK/Profiles/HoloLens2/) il controller della mano articolato è associato a *PokePointer,* *GrabPointer* e *DefaultControllerPointer* (ad esempio raggi mano).

> [!NOTE]
> MRTK fornisce un set di prefab puntatore in *Assets/MRTK/SDK/Features/UX/Prefabs/Pointers*. È possibile creare un nuovo prefab personalizzato, purché contenga uno degli script puntatore in *Assets/MRTK/SDK/Features/UX/Scripts/Pointers* o qualsiasi altro script che implementa [`IMixedRealityPointer`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointer) .

### <a name="default-pointer-classes"></a>Classi puntatore predefinite

Le classi seguenti sono i puntatori MRTK predefiniti disponibili e definiti nel profilo puntatore *MRTK* predefinito descritto in precedenza. Ogni prefab del puntatore fornito in *Assets/MRTK/SDK/Features/UX/Prefabs/Pointers* contiene uno dei componenti del puntatore collegati.

![Puntatori predefiniti MRTK](../images/input/pointers/MRTK_Pointers.png)

#### <a name="far-pointers"></a>Puntatori far

##### [`LinePointer`](xref:Microsoft.MixedReality.Toolkit.Input.LinePointer)

 *LinePointer*, una classe puntatore di base, disegna una linea dall'origine dell'input (ad esempio il controller) nella direzione del puntatore e supporta un singolo ray cast in questa direzione. In genere, le classi figlio, ad esempio e i puntatori di teletrasporto, vengono create e utilizzate (che disegnano anche linee per indicare dove finirà il teletrasporto) anziché questa classe che fornisce principalmente funzionalità [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) comuni.

Per i controller del movimento come in Oculus, Vive e Windows Mixed Reality, la rotazione corrisponderà alla rotazione del controller. Per altri controller, HoloLens 2 mani articolate, la rotazione corrisponde alla posizione di puntamento fornita dal sistema della mano.

<img src="../images/pointers/MRTK_Pointers_Line.png" width="400" alt="MRTK Pointer Line">

##### [`CurvePointer`](xref:Microsoft.MixedReality.Toolkit.Input.CurvePointer)

*CurvePointer* estende la *classe LinePointer* consentendo di eseguire raggi in più passaggi lungo una curva. Questa classe di puntatore di base è utile per le istanze curve, ad esempio i puntatori di teletrasporto in cui la linea si sposta in modo coerente in una parabola.

##### [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer)

L'implementazione *di ShellHandRayPointer,* che si estende da , viene usata come impostazione predefinita per il [`LinePointer`](xref:Microsoft.MixedReality.Toolkit.Input.MousePointer) profilo *puntatore MRTK.* Il prefab *DefaultControllerPointer* implementa la [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) classe .

##### [`GGVPointer`](xref:Microsoft.MixedReality.Toolkit.Input.GGVPointer)

Noto anche come puntatore *GGV (Gaze/Gesture/Voice),* GGVPointer consente di eseguire interazioni con aspetto e tocco HoloLens uno stile, principalmente tramite l'interazione di selezione dello sguardo fisso e dell'aria o sguardo fisso e voce. La posizione e la direzione dell'indicatore di misura GGV sono guidate dalla posizione e dalla rotazione della testa.

##### [`TouchPointer`](xref:Microsoft.MixedReality.Toolkit.Input.TouchPointer)

*TouchPointer è* responsabile dell'uso dell'input Touch di Unity,ad esempio il touchscreen. Si tratta di "interazioni da lontano" perché l'atto di toccare lo schermo proietta un raggio dalla fotocamera a una posizione potenzialmente distante nella scena.

##### [`MousePointer`](xref:Microsoft.MixedReality.Toolkit.Input.MousePointer)

*MousePointer alimenta un* raycast da schermo a mondo per interazioni da lontano, ma per il mouse anziché per il tocco.

![Puntatore del mouse](../images/pointers/MRTK_MousePointer.png)

> [!NOTE]
> Il supporto del mouse non è disponibile per impostazione predefinita in MRTK, ma *può* essere abilitato aggiungendo un nuovo provider di dati di input di tipo al profilo di input MRTK e assegnando al provider di [`MouseDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.MouseDeviceManager) [`MixedRealityMouseInputProfile`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityMouseInputProfile) dati.

#### <a name="near-pointers"></a>Puntatori vicini

##### [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer)

*[PokePointer viene usato](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer)* per interagire con gli oggetti gioco che supportano "near interaction touchable". che sono GameObject a cui è associato uno [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) script. Nel caso di UnityUI, questo puntatore cerca NearInteractionTouchableUnityUIs.  PokePointer usa SphereCast per determinare l'elemento toccabile più vicino e viene usato per alimentare elementi come i pulsanti a pressione.

 Quando si configura GameObject con il componente , assicurarsi di configurare il parametro localForward in modo che punti all'esterno della parte anteriore del pulsante o di un altro oggetto che deve [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) essere reso  toccabile. Assicurarsi anche che i limiti del *toccabile* corrispondano ai limiti dell'oggetto toccabile.

Proprietà utili del puntatore Poke:

- *TouchableDistance:* distanza massima con cui è possibile interagire con una superficie toccabile
- *Oggetti visivi: oggetto* gioco usato per eseguire il rendering dell'oggetto visivo punta del dito (l'anello sul dito, per impostazione predefinita).
- *Linea:* linea facoltativa da disegnare dalla punta del dito alla superficie di input attiva.
- *Poke Layer Masks (Maschera livello poke)* - Matrice con priorità di LayerMasks per determinare i GameObject possibili con cui il puntatore può interagire e l'ordine di interazione da provare. Si noti che un GameObject deve avere anche un componente per interagire con `NearInteractionTouchable` un puntatore poke.

<img src="../images/pointers/MRTK_PokePointer.png" width="400" alt="Poke Pointer">

##### [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer)

*[SpherePointer](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer)* usa [UnityEngine.Physics.OverlapSphere](https://docs.unity3d.com/ScriptReference/Physics.OverlapSphere.html) per identificare l'oggetto più vicino per l'interazione, utile per l'input [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) "afferrabile", ad esempio `ManipulationHandler` . Analogamente alla coppia funzionale, per poter interagire con l'indicatore di misura Sphere, l'oggetto gioco deve contenere un componente [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) / [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) che rappresenta lo [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) script.

<img src="../images/pointers/MRTK_GrabPointer.jpg" width="400" alt="Grab Pointer">

Proprietà utili del puntatore sphere:

- *Sphere Cast Radius (Raggio* cast sfera): raggio della sfera usata per eseguire una query per gli oggetti afferrabili.
- *Near Object Margin*(Margine oggetto vicino): distanza sopra il raggio del cast di sfera per eseguire una query per rilevare se un oggetto si trova vicino al puntatore. Il raggio totale di rilevamento di oggetti vicini è Raggio del cast di sfera + Margine oggetto vicino
- *Near Object Sector Angle :* angolo intorno all'asse in avanti del puntatore per l'esecuzione di query per oggetti vicini. Rende la `IsNearObject` funzione di query come un cono. Per impostazione predefinita, questa opzione è impostata su 66 gradi in modo che corrisponda al comportamento di Hololens 2

![Puntatore sphere modificato per eseguire una query solo per gli oggetti nella direzione avanti](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

- *Near Object Smoothing Factor (Fattore* di smussamento oggetti vicino): fattore di smussamento per il rilevamento di oggetti vicini. Se viene rilevato un oggetto nel raggio dell'oggetto vicino, il raggio sottoposto a query diventa Raggio oggetto vicino * (1 + Fattore di smussamento dell'oggetto vicino) per ridurre la sensibilità e rendere più difficile per un oggetto lasciare l'intervallo di rilevamento.
- *Grab Layer Masks (Afferra* maschere livello) - Matrice di LayerMasks classificata in ordine di priorità per determinare i GameObject possibili con cui il puntatore può interagire e l'ordine di interazione da provare. Si noti che un GameObject deve avere anche un `NearInteractionGrabbable` oggetto per interagire con un SpherePointer.
    > [!NOTE]
    > Il livello di consapevolezza spaziale è disabilitato nel prefab GrabPointer predefinito fornito da MRTK. Questa operazione viene eseguita per ridurre l'impatto sulle prestazioni dell'esecuzione di una query di sovrapposizione della sfera con la mesh spaziale. È possibile abilitarla modificando il prefab GrabPointer.
- *Ignore Colliders Not in FOV* (Ignora collisori non presenti nell'oggetto visivo) - Indica se ignorare i collisori che possono essere vicini all'indicatore di misura, ma non effettivamente nell'oggetto visivo.
Ciò può impedire afferramenti accidentali e consentirà l'attivazione dei raggi della mano quando potresti essere vicino a un afferrabile, ma non puoi vederlo. La *fov visuale* viene definita tramite un cono anziché il frustum tipico per motivi di prestazioni. Questo cono è centrato e orientato allo stesso modo del frustum della fotocamera con un raggio uguale alla metà dell'altezza di visualizzazione (o fov verticale).

<img src="../images/input/pointers/SpherePointer_VisualFOV.png" width="200" alt="Sphere Pointer">

#### <a name="teleport-pointers"></a>Puntatori di teletrasporto

- [`TeleportPointer`](xref:Microsoft.MixedReality.Toolkit.Teleport.TeleportPointer) genererà una richiesta di teletrasporto quando viene eseguita un'azione ,ad esempio il pulsante teletrasporto è premuto) per spostare l'utente.
- [`ParabolicTeleportPointer`](xref:Microsoft.MixedReality.Toolkit.Teleport.ParabolicTeleportPointer) genererà una richiesta di teletrasporto quando viene eseguita un'azione ,ad esempio il pulsante di teletrasporto è premuto) con un raycast a linea parabolica per spostare l'utente.

<img src="../images/pointers/MRTK_Pointers_Parabolic.png" width="400" alt="Pointer Parabolic">

## <a name="pointer-support-for-mixed-reality-platforms"></a>Supporto dei puntatori per le piattaforme di realtà mista

La tabella seguente contiene informazioni dettagliate sui tipi di puntatore usati in genere per le piattaforme comuni in MRTK. NOTA: è possibile aggiungere tipi di puntatore diversi a queste piattaforme. Ad esempio, è possibile aggiungere un puntatore Poke o Sphere alla realtà virtuale. Inoltre, i dispositivi VR con un game pad possono usare il puntatore GGV.

|       Puntatore              | OpenVR  | Windows Mixed Reality | HoloLens 1 | HoloLens 2 |
|---------------------|---------|-----------------------|------------|------------|
| ShellHandRayPointer | Valido   | Valido                 |            | Valido      |
| TeleportPointer     | Valido   | Valido                 |            |            |
| GGVPointer          |         |                       | Valido      |            |
| SpherePointer       |         |                       |            | Valido      |
| PokePointer         |         |                       |            | Valido      |

## <a name="pointer-interactions-via-code"></a>Interazioni dei puntatori tramite codice

### <a name="pointer-event-interfaces"></a>Interfacce di evento del puntatore

Gli oggetti MonoBehaviour che implementano una o più delle interfacce seguenti e vengono assegnati a un oggetto GameObject con un riceveranno eventi di interazione del puntatore in base a quanto definito `Collider` dall'interfaccia associata.

| Event | Descrizione | Gestore |
| --- | --- | --- |
| Prima della modifica dello stato attivo/modifica dello stato attivo | Generato sull'oggetto gioco che perde lo stato attivo e su quello che lo ottiene ogni volta che un puntatore cambia lo stato attivo. | [`IMixedRealityFocusChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusChangedHandler) |
Invio/uscita dello stato attivo | Generato sull'oggetto di gioco che ottiene lo stato attivo quando il primo puntatore entra in esso e su quello che perde lo stato attivo quando l'ultimo puntatore lo lascia. | [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler)
Puntatore verso il basso/trascinato/verso l'alto/su | Generato per segnalare la pressione del puntatore, il trascinamento e il rilascio. | [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler)
Tocco avviato/aggiornato/completato | Generato da puntatori in grado di riconoscere il tocco, ad esempio [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) per segnalare l'attività di tocco. | [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)

> [!NOTE]
> [`IMixedRealityFocusChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusChangedHandler) e [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler) devono essere gestiti negli oggetti su cui vengono generati. È possibile ricevere eventi di stato attivo a livello globale, ma, a differenza di altri eventi di input, il gestore eventi globale non blocca la ricezione di eventi in base al focus (l'evento verrà ricevuto sia dal gestore globale che da un oggetto corrispondente nello stato attivo).

#### <a name="pointer-input-events-in-action"></a>Eventi di input del puntatore in azione

Gli eventi di input del puntatore vengono riconosciuti e gestiti dal sistema di input MRTK in modo analogo agli [eventi di input normali.](input-events.md#input-events-in-action) La differenza è che gli eventi di input del puntatore vengono gestiti solo dal GameObject nello stato attivo dal puntatore che ha generato l'evento di input, nonché da qualsiasi gestore di input globale. Gli eventi di input regolari vengono gestiti da GameObjects nello stato attivo per tutti i puntatori attivi.

1. Il sistema di input MRTK riconosce che si è verificato un evento di input
1. Il sistema di input MRTK genera la funzione di interfaccia pertinente per l'evento di input a tutti i gestori di input globali registrati
1. Il sistema di input determina quale GameObject è attivo per il puntatore che ha generato l'evento
    1. Il sistema di input usa il sistema di eventi di Unity per impostare la funzione di interfaccia pertinente per tutti i componenti corrispondenti [nell'oggetto](https://docs.unity3d.com/Manual/EventSystem.html) GameObject attivo
    1. Se in qualsiasi momento un evento di input è stato contrassegnato come [usato,](input-events.md#how-to-stop-input-events)il processo terminerà e nessun altro GameObject riceverà callback.
        - Esempio: i componenti che implementano l'interfaccia verranno cercati per un [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) GameObject che ottiene o perde lo stato attivo
        - Nota: il sistema di eventi Unity verrà visualizzato per cercare l'oggetto GameObject padre se non vengono trovati componenti corrispondenti all'interfaccia desiderata nell'oggetto GameObject corrente.
1. Se non sono registrati gestori di input globali e non viene trovato alcun GameObject con un componente/interfaccia corrispondente, il sistema di input chiamerà ogni gestore di input registrato di fallback

#### <a name="example"></a>Esempio

Di seguito è riportato uno script di esempio che modifica il colore del renderer associato quando un puntatore assume o lascia lo stato attivo o quando un puntatore seleziona l'oggetto.

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

È possibile raccogliere tutti i puntatori attualmente attivi scorrendo in ciclo le origini di input disponibili, ad esempio controller e input disponibili) per individuare i puntatori associati.

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

Gli sviluppatori possono sottoscrivere l'evento FocusProviders PrimaryPointerChanged per ricevere una notifica quando il puntatore primario nello stato attivo viene modificato. Questo può essere estremamente utile per identificare se l'utente sta attualmente interagendo con una scena tramite lo sguardo fisso o un raggio della mano o un'altra origine di input.

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

La `PrimaryPointerExample` scena (Assets/MRTK/Examples/Demos/Input/Scenes/PrimaryPointer) illustra come usare per gli eventi per rispondere a un nuovo [`PrimaryPointerChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.PrimaryPointerChangedHandler) puntatore primario.

<img src="../images/pointers/PrimaryPointerExample.png" style="max-width:100%;" alt="Primary Pointer Example">

### <a name="pointer-result"></a>Risultato del puntatore

La proprietà pointer [`Result`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointer.Result) contiene il risultato corrente per la query della scena usata per determinare l'oggetto con lo stato attivo. Per un puntatore raycast, come quelli creati per impostazione predefinita per i controller di movimento, l'input dello sguardo fisso e i raggi della mano, conterrà la posizione e la normale dell'hit raycast.

```c#
private void IMixedRealityPointerHandler.OnPointerClicked(MixedRealityPointerEventData eventData)
{
    var result = eventData.Pointer.Result;
    var spawnPosition = result.Details.Point;
    var spawnRotation = Quaternion.LookRotation(result.Details.Normal);
    Instantiate(MyPrefab, spawnPosition, spawnRotation);
}
```

La `PointerResultExample` scena (Assets/MRTK/Examples/Demos/Input/Scenes/PointerResult/PointerResultExample.unity) illustra come usare il puntatore per generare un oggetto nella posizione di [`Result`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointer.Result) hit.

<img src="../images/input/PointerResultExample.png" style="max-width:100%;" alt="Pointer Result">

### <a name="disable-pointers"></a>Disabilitare i puntatori

Per attivare e disattivare i puntatori (ad esempio, per disabilitare il raggio della mano), impostare per un determinato tipo [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) di puntatore tramite [`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) .

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

Vedere [`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) e per altri [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) esempi.

## <a name="pointer-interactions-via-editor"></a>Interazioni con i puntatori tramite editor

Per gli eventi puntatore gestiti da , MRTK offre maggiore praticità sotto forma di componente, che consente di gestire gli eventi puntatore [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) [`PointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.PointerHandler) direttamente tramite eventi Unity.

<img src="../images/pointers/PointerHandler.png" style="max-width:100%;" alt="Pointer Handler">

## <a name="pointer-extent"></a>Extent del puntatore

I puntatori lontano hanno impostazioni che limitano la distanza in cui verranno raggiati e interagiranno con altri oggetti nella scena.
Per impostazione predefinita, questo valore è impostato su 10 metri. Questo valore è stato scelto per rimanere coerente con il comportamento della HoloLens shell.

È possibile modificare questa impostazione aggiornando i campi del `DefaultControllerPointer` componente [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) prefab:

*Extent puntatore:* controlla la distanza massima con cui i puntatori interagiranno.

*Estensione puntatore predefinita:* controlla la lunghezza del raggio/linea del puntatore di cui verrà eseguito il rendering quando il puntatore non interagisce con alcun elemento.

## <a name="see-also"></a>Vedi anche

- [Architettura dei puntatori](../../architecture/controllers-pointers-and-focus.md)
- [Eventi di input](input-events.md)
