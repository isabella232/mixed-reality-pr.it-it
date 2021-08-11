---
title: Creazione di un provider di dati del sistema di input
description: documentazione per creare il sistema di input e il provider di dati in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 391aa477bb09fa2dec2b3bcb26bad813c715ee03eeb0dc03dcbc9048ae318295
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223990"
---
# <a name="creating-an-input-system-data-provider"></a>Creazione di un provider di dati del sistema di input

Il sistema di input Toolkit realtà mista è un sistema estendibile per abilitare il supporto dei dispositivi di input. Per aggiungere il supporto per una nuova piattaforma hardware, potrebbe essere necessario un provider di dati di input personalizzato.

Questo articolo descrive come creare provider di dati personalizzati, denominati anche gestori di dispositivi, per il sistema di input. Il codice di esempio illustrato di seguito è da [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) .

> Il codice completo usato in questo esempio è disponibile nella cartella MRTK/Providers/WindowsMixedReality.

## <a name="namespace-and-folder-structure"></a>Spazio dei nomi e struttura di cartelle

I provider di dati possono essere distribuiti come componente aggiuntivo di terze parti o come parte di Microsoft Mixed Reality Toolkit. Il processo di approvazione per l'invio di nuovi provider di dati al modulo MRTK varia caso per caso e verrà comunicato al momento della proposta iniziale.

> [!Important]
> Se un provider di dati del sistema di input viene inviato [al repository Toolkit realtà](https://github.com/Microsoft/MixedRealityToolkit-Unity)mista, lo spazio dei nomi deve iniziare con Microsoft.MixedReality.  Toolkit (ad esempio: Microsoft.MixedReality.Toolkit. WindowsMixedReality) e il codice deve trovarsi in una cartella sotto MRTK/Providers (ad esempio: MRTK/Providers/WindowsMixedReality).

### <a name="namespace"></a>Spazio dei nomi

I provider di dati devono disporre di uno spazio dei nomi per attenuare potenziali conflitti di nomi. È consigliabile che lo spazio dei nomi includa i componenti seguenti.

- Nome azienda
- Area funzionale

Ad esempio, un provider di dati di input creato dalla società Contoso può essere "Contoso.MixedReality. Toolkit. Input".

### <a name="recommended-folder-structure"></a>Struttura di cartelle consigliata

È consigliabile che il codice sorgente per i provider di dati sia disponibile in una gerarchia di cartelle, come illustrato nell'immagine seguente.

![Esempio di struttura di cartelle](../images/input/ExampleProviderFolderStructure.png)

Dove ContosoInput contiene l'implementazione del provider di dati, la cartella Editor contiene il controllo (e qualsiasi altro codice specifico dell'editor unity), la cartella Textures contiene immagini dei controller supportati e Profiles contiene uno o più profili predefiniti.

> [!Note]
> Alcune immagini comuni del controller sono disponibili nella cartella MixedRealityToolkit\StandardAssets\Textures.

## <a name="implement-the-data-provider"></a>Implementare il provider di dati

### <a name="specify-interface-andor-base-class-inheritance"></a>Specificare l'ereditarietà dell'interfaccia e/o della classe di base

Tutti i provider di dati del sistema di input devono implementare l'interfaccia , che [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) specifica la funzionalità minima richiesta dal sistema di input. La base MRTK include la [`BaseInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) classe che fornisce un'implementazione predefinita di questa funzionalità richiesta. Per i dispositivi che si basano sulla classe UInput di Unity, la [`UnityJoystickManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) classe può essere usata come classe di base.

> [!Note]
> Le `BaseInputDeviceManager` classi e forniscono `UnityJoystickManager` l'implementazione `IMixedRealityInputDeviceManager` richiesta.

```c#
public class WindowsMixedRealityDeviceManager :
    BaseInputDeviceManager,
    IMixedRealityCapabilityCheck
{ }
```

> `IMixedRealityCapabilityCheck` viene usato da per indicare che fornisce il supporto per un set di funzionalità di input, in particolare mani articolate, mani con movimento fisso-movimento e controller `WindowsMixedRealityDeviceManager` di movimento.

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a>Applicare l'attributo MixedRealityDataProvider

Un passaggio chiave della creazione di un provider di dati del sistema di input consiste nell'applicare [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) l'attributo alla classe . Questo passaggio abilita l'impostazione del profilo e della piattaforma predefiniti per il provider, se selezionato nel profilo di sistema di input.

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

Dopo aver definito la classe, il passaggio successivo consiste nel fornire l'implementazione [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) dell'interfaccia .

> [!Note]
> La `BaseInputDeviceManager` classe , tramite la classe , fornisce solo `BaseService` implementazioni vuote per i metodi `IMixedRealityDataProvider` . I dettagli di questi metodi sono in genere specifici del provider di dati.

I metodi che devono essere implementati dal provider di dati sono:

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

### <a name="implement-the-data-provider-logic"></a>Implementare la logica del provider di dati

Il passaggio successivo consiste nell'aggiungere la logica per la gestione dei dispositivi di input, inclusi i controller da supporto.

### <a name="implement-the-controller-classes"></a>Implementare le classi controller

 L'esempio di `WindowsMixedRealityDeviceManager` definisce e implementa le classi controller seguenti.

> Il codice sorgente per ognuna di queste classi è disponibile nella cartella MRTK/Providers/WindowsMixedReality.

- WindowsMixedRealityArticulatedHand.cs
- WindowsMixedRealityController.cs
- WindowsMixedRealityGGVHand.cs

> [!Note]
> Non tutti i gestori di dispositivi supporteranno più tipi di controller.

#### <a name="apply-the-mixedrealitycontroller-attribute"></a>Applicare l'attributo MixedRealityController

Applicare quindi [`MixedRealityController`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityControllerAttribute) l'attributo alla classe . Questo attributo specifica il tipo di controller (ad esempio: mano articolata), la mano (ad esempio, sinistra o destra) e un'immagine del controller facoltativa.

```c#
[MixedRealityController(
    SupportedControllerType.WindowsMixedReality,
    new[] { Handedness.Left, Handedness.Right },
    "StandardAssets/Textures/MotionController")]
{ }
```

#### <a name="configure-the-interaction-mappings"></a>Configurare i mapping di interazione

Il passaggio successivo consiste nel definire il set di mapping di interazione supportati dal controller. Per i dispositivi che ricevono i dati tramite la classe Input di Unity, lo strumento di mapping del [controller](../tools/controller-mapping-tool.md) è una risorsa utile per confermare i mapping degli assi e dei pulsanti corretti da assegnare alle interazioni.

L'esempio seguente è abbreviato dalla classe `GenericOpenVRController` , che si trova nella cartella MRTK/Providers/OpenVR.

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
>La [`ControllerMappingLibrary`](xref:Microsoft.MixedReality.Toolkit.Input.ControllerMappingLibrary) classe fornisce costanti simboliche per le definizioni di asse di input e pulsante di Unity.

### <a name="raise-notification-events"></a>Generare eventi di notifica

Per consentire alle applicazioni di rispondere all'input dell'utente, il provider di dati genera eventi di notifica corrispondenti alle modifiche dello stato del controller, come definito nelle [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) interfacce e .

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

Per i controlli analoghi ,ad esempio la posizione del touchpad, deve essere generato l'evento InputChanged.

```c#
InputSystem?.RaisePositionInputChanged(InputSource, ControllerHandedness, interactionMapping.MixedRealityInputAction, interactionSourceState.touchpadPosition);
```

### <a name="add-unity-profiler-instrumentation"></a>Aggiungere la strumentazione del profiler Unity

Le prestazioni sono fondamentali nelle applicazioni di realtà mista. Ogni componente aggiunge una certa quantità di overhead di cui le applicazioni devono essere conto. A questo scopo, è importante che tutti i provider di dati di input contengano strumentazione del profiler Unity nel ciclo interno e percorsi di codice usati di frequente.

È consigliabile implementare il modello utilizzato da MRTK durante la strumentazione di provider personalizzati.

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
> Il nome usato per identificare il marcatore del profiler è arbitrario. MrTK usa il modello seguente.
>
> "[product] className.methodName - nota facoltativa"
>
> È consigliabile che i provider di dati personalizzati seguano un modello simile per semplificare l'identificazione di componenti e metodi specifici durante l'analisi delle tracce.

## <a name="create-the-profile-and-inspector"></a>Creare il profilo e il controllo

Nel modello di realtà mista Toolkit i provider di dati vengono configurati tramite [profili](../profiles/profiles.md).

I provider di dati con opzioni di configurazione aggiuntive (ad esempio [InputSimulationService](../input-simulation/input-simulation-service.md)) devono creare un profilo e un controllo per consentire ai clienti di modificare il comportamento in base alle esigenze dell'applicazione.

> Il codice completo per l'esempio in questa sezione è disponibile in MRTK. Cartella Services/InputSimulation.

### <a name="define-the-profile"></a>Definire il profilo

Il contenuto del profilo deve rispecchiare le proprietà accessibili dell'osservatore (ad esempio, intervallo di aggiornamento). Tutte le proprietà configurabili dall'utente definite in ogni interfaccia devono essere contenute nel profilo.

```c#
[CreateAssetMenu(
    menuName = "Mixed Reality Toolkit/Profiles/Mixed Reality Simulated Input Profile",
    fileName = "MixedRealityInputSimulationProfile",
    order = (int)CreateProfileMenuItemIndices.InputSimulation)]
public class MixedRealityInputSimulationProfile : BaseMixedRealityProfile
{ }
```

L'attributo può essere applicato alla classe del profilo per consentire ai clienti di creare un'istanza del profilo usando il menu Create `CreateAssetMenu` **> Assets > Mixed Reality Toolkit > Profiles** .

### <a name="implement-the-inspector"></a>Implementare il controllo

I controlli profilo sono l'interfaccia utente per la configurazione e la visualizzazione del contenuto del profilo. Ogni controllo del profilo deve estendere la [classe 'BaseMixedRealityToolkitConfigurationProfileInspector.](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector)

```c#
[CustomEditor(typeof(MixedRealityInputSimulationProfile))]
public class MixedRealityInputSimulationProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
{ }
```

`CustomEditor`L'attributo indica a Unity il tipo di asset a cui si applica il controllo.

## <a name="create-assembly-definitions"></a>Creare definizioni di assembly

L'Toolkit di realtà mista usa i file di definizione dell'assembly ([asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) per specificare le dipendenze tra i componenti e per aiutare Unity a ridurre il tempo di compilazione.

È consigliabile creare file di definizione dell'assembly per tutti i provider di dati e i relativi componenti dell'editor.

Usando la [struttura di](#recommended-folder-structure) cartelle nell'esempio precedente, saranno presenti due file asmdef per il provider di dati ContosoInput.

La prima definizione di assembly è per il provider di dati. Per questo esempio, si chiamerà ContosoInput e si trova nella cartella ContosoInput dell'esempio.
Questa definizione di assembly deve specificare una dipendenza da Microsoft.MixedReality. Toolkit e qualsiasi altro assembly da cui dipende.

La definizione dell'assembly ContosoInputEditor specificherà il controllo del profilo e qualsiasi codice specifico dell'editor. Questo file deve trovarsi nella cartella radice del codice dell'editor. In questo esempio il file si trova nella cartella ContosoInput\Editor. Questa definizione di assembly conterrà un riferimento all'assembly ContosoInput, nonché:

- Microsoft.MixedReality. Toolkit
- Microsoft.MixedReality. Toolkit. Editor.Inspectors
- Microsoft.MixedReality. Toolkit. Editor.Utilities

## <a name="register-the-data-provider"></a>Registrare il provider di dati

Dopo la creazione, il provider di dati può essere registrato con il sistema di input e usato nell'applicazione.

![Provider di dati del sistema di input registrati](../images/input/RegisteredServiceProviders.PNG)

## <a name="packaging-and-distribution"></a>Creazione di pacchetti e distribuzione

I provider di dati distribuiti come componenti di terze parti hanno i dettagli specifici della creazione di pacchetti e della distribuzione lasciati alle preferenze dello sviluppatore. È probabile che la soluzione più comune sia generare un file unitypackage e distribuirsi tramite Unity Asset Store.

Se un provider di dati viene inviato e accettato come parte del pacchetto Microsoft Mixed Reality Toolkit, il team di Microsoft MRTK lo inserirà e lo distribuirà come parte delle offerte MRTK.

## <a name="see-also"></a>Vedi anche

- [Sistema di input](overview.md)
- [Classe `BaseInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager)
- [`IMixedRealityInputDeviceManager` Interfaccia](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager)
- [`IMixedRealityInputHandler` Interfaccia](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler)
- [`IMixedRealityInputHandler<T>` Interfaccia](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1)
- [`IMixedRealityDataProvider` Interfaccia](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [`IMixedRealityCapabilityCheck` Interfaccia](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [Strumento di mapping dei controller](../tools/controller-mapping-tool.md)
