---
title: CreateInputDataProvider
description: documentazione per creare il sistema di input e il provider di dati in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 7a1a744602f791f26a4c1497c0853f0d370914b2
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104682344"
---
# <a name="creating-an-input-system-data-provider"></a>Creazione di un provider di dati di sistema di input

Il sistema di input del Toolkit di realtà mista è un sistema estensibile per abilitare il supporto dei dispositivi di input. Per aggiungere il supporto per una nuova piattaforma hardware, potrebbe essere necessario un provider di dati di input personalizzato.

Questo articolo descrive come creare provider di dati personalizzati, denominati anche gestione dispositivi, per il sistema di input. Il codice di esempio illustrato di seguito è da [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) .

> Il codice completo usato in questo esempio si trova nella cartella MRTK/Providers/WindowsMixedReality.

## <a name="namespace-and-folder-structure"></a>Struttura dello spazio dei nomi e della cartella

I provider di dati possono essere distribuiti come componente aggiuntivo di terze parti o come parte di Microsoft Mixed Reality Toolkit. Il processo di approvazione per gli invii di nuovi provider di dati alla MRTK varia a seconda del caso e verrà comunicato al momento della proposta iniziale di.

> [!Important]
> Se un provider di dati di sistema di input viene inviato al [repository del Toolkit di realtà mista](https://github.com/Microsoft/MixedRealityToolkit-Unity), lo spazio dei nomi **deve** iniziare con Microsoft. MixedReality. Toolkit (ad esempio Microsoft. MixedReality. Toolkit. WindowsMixedReality) e il codice deve trovarsi in una cartella sotto MRTK/provider (ad esempio, MRTK/Providers/WindowsMixedReality).

### <a name="namespace"></a>Spazio dei nomi

È necessario che i provider di dati dispongano di uno spazio dei nomi per attenuare i potenziali conflitti di nomi. È consigliabile che lo spazio dei nomi includa i componenti seguenti.

- Nome azienda
- Area funzionale

Un provider di dati di input creato dalla società Contoso, ad esempio, può essere "contoso. MixedReality. Toolkit. input".

### <a name="recommended-folder-structure"></a>Struttura di cartelle consigliata

È consigliabile che il codice sorgente per i provider di dati venga disposto in una gerarchia di cartelle, come illustrato nella figura seguente.

![Esempio di struttura di cartelle](../images/input/ExampleProviderFolderStructure.png)

Dove ContosoInput contiene l'implementazione del provider di dati, la cartella dell'editor contiene il controllo (e qualsiasi altro codice specifico dell'editor Unity), la cartella trame contiene immagini dei controller supportati e i profili contengono uno o più profili predefiniti.

> [!Note]
> Alcune immagini del controller comuni si trovano nella cartella MixedRealityToolkit\StandardAssets\Textures.

## <a name="implement-the-data-provider"></a>Implementare il provider di dati

### <a name="specify-interface-andor-base-class-inheritance"></a>Specificare l'ereditarietà dell'interfaccia e/o della classe base

Tutti i provider di dati di sistema di input devono implementare l' [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) interfaccia, che specifica la funzionalità minima richiesta dal sistema di input. MRTK Foundation include la [`BaseInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) classe che fornisce un'implementazione predefinita di questa funzionalità richiesta. Per i dispositivi che si basano sulla classe UInput di Unity, la [`UnityJoystickManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) classe può essere usata come classe di base.

> [!Note]
> Le `BaseInputDeviceManager` `UnityJoystickManager` classi e forniscono l' `IMixedRealityInputDeviceManager` implementazione richiesta.

```c#
public class WindowsMixedRealityDeviceManager :
    BaseInputDeviceManager,
    IMixedRealityCapabilityCheck
{ }
```

> `IMixedRealityCapabilityCheck` viene usato da `WindowsMixedRealityDeviceManager` per indicare che fornisce il supporto per un set di funzionalità di input, in particolare per le mani e i controller di movimento.

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a>Applicare l'attributo MixedRealityDataProvider

Un passaggio chiave per la creazione di un provider di dati di sistema di input consiste nell'applicare l' [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) attributo alla classe. Questo passaggio consente di impostare il profilo e le piattaforme predefiniti per il provider, quando è selezionato nel profilo di sistema di input.

```c#
[MixedRealityDataProvider(
    typeof(IMixedRealityInputSystem),
    SupportedPlatforms.WindowsUniversal,
    "Windows Mixed Reality Device Manager")]
public class WindowsMixedRealityDeviceManager :
    BaseInputDeviceManager,
    IMixedRealityCapabilityCheck
{ }
```

### <a name="implement-the-imixedrealitydataprovider-methods"></a>Implementare i metodi IMixedRealityDataProvider

Una volta definita la classe, il passaggio successivo consiste nel fornire l'implementazione dell' [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interfaccia.

> [!Note]
> La `BaseInputDeviceManager` classe, tramite la `BaseService` classe, fornisce solo implementazioni vuote per i `IMixedRealityDataProvider` metodi. I dettagli di questi metodi sono in genere specifici del provider di dati.

I metodi che devono essere implementati dal provider di dati sono:

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

### <a name="implement-the-data-provider-logic"></a>Implementare la logica del provider di dati

Il passaggio successivo consiste nell'aggiungere la logica per la gestione dei dispositivi di input, inclusi tutti i controller da supportare.

### <a name="implement-the-controller-classes"></a>Implementare le classi controller

 Nell'esempio di vengono `WindowsMixedRealityDeviceManager` definite e implementate le classi controller seguenti.

> Il codice sorgente per ognuna di queste classi è reperibile nella cartella MRTK/Providers/WindowsMixedReality.

- WindowsMixedRealityArticulatedHand. cs
- WindowsMixedRealityController. cs
- WindowsMixedRealityGGVHand. cs

> [!Note]
> Non tutte le gestioni dispositivi supportano più tipi di controller.

#### <a name="apply-the-mixedrealitycontroller-attribute"></a>Applicare l'attributo MixedRealityController

Applicare quindi l' [`MixedRealityController`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityControllerAttribute) attributo alla classe. Questo attributo specifica il tipo di controller (ad esempio, la mano articolata), la manualità (ad esempio, a sinistra o a destra) e un'immagine del controller facoltativa.

```c#
[MixedRealityController(
    SupportedControllerType.WindowsMixedReality,
    new[] { Handedness.Left, Handedness.Right },
    "StandardAssets/Textures/MotionController")]
{ }
```

#### <a name="configure-the-interaction-mappings"></a>Configurare i mapping di interazione

Il passaggio successivo consiste nel definire il set di mapping di interazione supportati dal controller. Per i dispositivi che ricevono i dati tramite la classe di input di Unity, lo [strumento di mapping del controller](../tools/ControllerMappingTool.md) è una risorsa utile per confermare l'asse corretto e i mapping dei pulsanti da assegnare alle interazioni.

L'esempio seguente è abbreviato dalla `GenericOpenVRController` classe, disponibile nella cartella MRTK/Providers/OpenVR.

```c#
public override MixedRealityInteractionMapping[] DefaultLeftHandedInteractions => new[]
{
    // Controller Pose
    new MixedRealityInteractionMapping(0, "Spatial Pointer", AxisType.SixDof, DeviceInputType.SpatialPointer, MixedRealityInputAction.None),
    // Left Trigger Squeeze
    new MixedRealityInteractionMapping(1, "Trigger Position", AxisType.SingleAxis, DeviceInputType.Trigger, ControllerMappingLibrary.AXIS_9),
    // Left Trigger Press (Select)
    new MixedRealityInteractionMapping(2, "Trigger Press (Select)", AxisType.Digital, DeviceInputType.TriggerPress, KeyCode.JoystickButton14),
};
```

>[!Note]
>La [`ControllerMappingLibrary`](xref:Microsoft.MixedReality.Toolkit.Input.ControllerMappingLibrary) classe fornisce costanti simboliche per l'asse di input Unity e le definizioni dei pulsanti.

### <a name="raise-notification-events"></a>Genera eventi di notifica

Per consentire alle applicazioni di rispondere all'input dell'utente, il provider di dati genera eventi di notifica corrispondenti alle modifiche dello stato del controller come definito nelle [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) interfacce e.

Per i controlli di tipo digitale (pulsante), generare gli eventi OnInputDown e OnInputUp.

```c#
// inputAction is the input event that is to be raised.
if (interactionSourceState.touchpadPressed)
{
    InputSystem?.RaiseOnInputDown(InputSource, ControllerHandedness, inputAction);
}
else
{
    InputSystem?.RaiseOnInputUp(InputSource, ControllerHandedness, inputAction);
}
```

Per i controlli analoghi, ad esempio la posizione del touchpad, viene generato l'evento InputChanged.

```c#
InputSystem?.RaisePositionInputChanged(InputSource, ControllerHandedness, interactionMapping.MixedRealityInputAction, interactionSourceState.touchpadPosition);
```

### <a name="add-unity-profiler-instrumentation"></a>Aggiungere la strumentazione del profiler Unity

Le prestazioni sono cruciali nelle applicazioni di realtà mista. Ogni componente aggiunge una certa quantità di overhead per cui le applicazioni devono tenere conto. A questo scopo, è importante che tutti i provider di dati di input contengano la strumentazione del profiler Unity nel ciclo interno e i percorsi di codice utilizzati di frequente.

È consigliabile implementare il modello utilizzato da MRTK quando si instrumentano provider personalizzati.

```c#
        private static readonly ProfilerMarker GetOrAddControllerPerfMarker = new ProfilerMarker("[MRTK] WindowsMixedRealityDeviceManager.GetOrAddController");

        private async void GetOrAddController(InteractionSourceState interactionSourceState)
        {
            using (GetOrAddControllerPerfMarker.Auto())
            {
                // Code to be measured.
            }
        }
```

> [!Note]
> Il nome utilizzato per identificare il marcatore del profiler è arbitrario. MRTK usa il modello seguente.
>
> "[Product] nomeclasse. MethodName-nota facoltativa"
>
> È consigliabile che i provider di dati personalizzati seguano un modello simile per semplificare l'identificazione di componenti e metodi specifici durante l'analisi delle tracce.

## <a name="create-the-profile-and-inspector"></a>Creare il profilo e il controllo

Nel Toolkit per la realtà mista i provider di dati vengono configurati usando i [profili](../profiles/Profiles.md).

I provider di dati con opzioni di configurazione aggiuntive, ad esempio [InputSimulationService](../input-simulation/InputSimulationService.md), devono creare un profilo e un controllo per consentire ai clienti di modificare il comportamento per soddisfare al meglio le esigenze dell'applicazione.

> Il codice completo per l'esempio in questa sezione si trova in MRTK. Services/InputSimulation cartella.

### <a name="define-the-profile"></a>Definire il profilo

Il contenuto del profilo dovrebbe rispecchiare le proprietà accessibili dell'Observer (ad esempio, intervallo di aggiornamento). Tutte le proprietà configurabili dall'utente definite in ogni interfaccia devono essere contenute nel profilo.

```c#
[CreateAssetMenu(
    menuName = "Mixed Reality Toolkit/Profiles/Mixed Reality Simulated Input Profile",
    fileName = "MixedRealityInputSimulationProfile",
    order = (int)CreateProfileMenuItemIndices.InputSimulation)]
public class MixedRealityInputSimulationProfile : BaseMixedRealityProfile
{ }
```

L' `CreateAssetMenu` attributo può essere applicato alla classe profile per consentire ai clienti di creare un'istanza del profilo usando il menu **create > assets > Mixed Reality Toolkit > Profiles** .

### <a name="implement-the-inspector"></a>Implementare il controllo

I controlli profilo sono l'interfaccia utente per la configurazione e la visualizzazione del contenuto del profilo. Ogni controllo profilo deve estendere la classe [' BaseMixedRealityToolkitConfigurationProfileInspector '](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) .

```c#
[CustomEditor(typeof(MixedRealityInputSimulationProfile))]
public class MixedRealityInputSimulationProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
{ }
```

L' `CustomEditor` attributo informa Unity del tipo di asset a cui si applica il controllo.

## <a name="create-assembly-definitions"></a>Crea definizione/i assembly

Il Toolkit di realtà mista Usa i file di definizione di assembly (con[estensione asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) per specificare le dipendenze tra i componenti e per aiutare Unity a ridurre i tempi di compilazione.

Si consiglia di creare i file di definizione degli assembly per tutti i provider di dati e i relativi componenti dell'editor.

Usando la [struttura di cartelle](#recommended-folder-structure) nell'esempio precedente, sono presenti due file. asmdef per il provider di dati ContosoInput.

La prima definizione di assembly è per il provider di dati. Per questo esempio, viene chiamato ContosoInput e si trova nella cartella ContosoInput dell'esempio.
Questa definizione di assembly deve specificare una dipendenza da Microsoft. MixedReality. Toolkit e da tutti gli altri assembly da cui dipende.

La definizione dell'assembly ContosoInputEditor specifica il controllo del profilo e qualsiasi codice specifico dell'editor. Questo file deve trovarsi nella cartella radice del codice dell'editor. In questo esempio il file si trova nella cartella ContosoInput\Editor Questa definizione di assembly conterrà un riferimento all'assembly ContosoInput, oltre a:

- Microsoft. MixedReality. Toolkit
- Microsoft. MixedReality. Toolkit. Editor. Inspectors
- Microsoft. MixedReality. Toolkit. Editor. Utilities

## <a name="register-the-data-provider"></a>Registrare il provider di dati

Una volta creato, il provider di dati può essere registrato con il sistema di input e deve essere utilizzato nell'applicazione.

![Provider di dati di sistema di input registrati](../images/input/RegisteredServiceProviders.PNG)

## <a name="packaging-and-distribution"></a>Creazione di pacchetti e distribuzione

I provider di dati distribuiti come componenti di terze parti presentano i dettagli specifici della creazione di pacchetti e della distribuzione, a seconda delle preferenze dello sviluppatore. Probabilmente, la soluzione più comune consiste nel generare un file con estensione file unitypackage Tools e distribuirlo tramite l'archivio risorse di Unity.

Se un provider di dati viene inviato e accettato come parte del pacchetto Microsoft Mixed Reality Toolkit, il team di Microsoft MRTK lo comprimerà e lo distribuirà come parte delle offerte di MRTK.

## <a name="see-also"></a>Vedi anche

- [Sistema di input](Overview.md)
- [`BaseInputDeviceManager` classe](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager)
- [`IMixedRealityInputDeviceManager` interfaccia](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager)
- [`IMixedRealityInputHandler` interfaccia](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler)
- [`IMixedRealityInputHandler<T>` interfaccia](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1)
- [`IMixedRealityDataProvider` interfaccia](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [`IMixedRealityCapabilityCheck` interfaccia](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [Strumento di mapping controller](../tools/ControllerMappingTool.md)
