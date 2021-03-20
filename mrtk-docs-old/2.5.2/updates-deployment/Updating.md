---
title: Aggiornamento
description: Documentazione per la migrazione da una versione precedente di MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: ec6b73b32807ece66f75e11f49e44f16a254945e
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104685744"
---
# <a name="updating-the-microsoft-mixed-reality-toolkit"></a>Aggiornamento di Microsoft Mixed Reality Toolkit

- [Aggiornamento a una nuova versione di MRTK](#upgrading-to-a-new-version-of-mrtk)
- [da 2.3.0 a 2.4.0](#updating-230-to-240)
- [da 2.2.0 a 2.3.0](#updating-220-to-230)
- [da 2.1.0 a 2.2.0](#updating-210-to-220)
- [2.0.0 a 2.1.0](#updating-200-to-210)
- [Da RC2 a 2.0.0](#updating-rc2-to-200)

## <a name="upgrading-to-a-new-version-of-mrtk"></a>Aggiornamento a una nuova versione di MRTK

*Si consiglia vivamente di eseguire lo [strumento di migrazione](../features/tools/MigrationWindow.md) dopo aver ricevuto l'aggiornamento di MRTK per la* correzione automatica e l'aggiornamento dai componenti deprecati e la modifica delle modifiche di rilievo. Lo strumento di migrazione fa parte del pacchetto di **strumenti** .

Le istruzioni seguenti descrivono il percorso di aggiornamento da 2.4.0 a 2.5.0. Se il progetto si trova in 2.3.0 o versioni precedenti, leggere le modifiche [tra le versioni](#updating-230-to-240) per comprendere il percorso di aggiornamento o leggere le [istruzioni](https://microsoft.github.io/MixedRealityToolkit-Unity/version/releases/2.4.0/Documentation/Updating.html) della versione precedente per eseguire un aggiornamento versione per versione.

### <a name="unity-asset-unitypackage-files"></a>File di asset Unity (con estensione file unitypackage Tools)

Per il percorso di aggiornamento più semplice, seguire questa procedura.

1. Salvare una copia del progetto corrente, nel caso in cui si riscontrino eventuali strappi in qualsiasi punto della procedura di aggiornamento.
1. Chiudi Unity
1. All'interno della cartella *assets* , eliminare le cartelle **MRTK** seguenti, insieme ai relativi file con estensione meta (il progetto potrebbe non avere tutte le cartelle elencate)
    - MRTK/Core
    - MRTK/esempi
    - MRTK/estensioni
    > [!NOTE]
    > Se sono state installate estensioni aggiuntive, eseguire un backup prima di eliminare le cartelle.
    - MRTK/provider
    - MRTK/SDK
    - MRTK/servizi
    - MRTK/strumenti
    > [!IMPORTANT]
    > Non eliminare la cartella **MixedRealityToolkit. generated** o il relativo file con estensione meta.
1. Elimina la cartella della **libreria**
    > [!IMPORTANT]
    > Alcuni strumenti di Unity, ad esempio Unity collab, salvano le informazioni di configurazione nella cartella della libreria. Se si usa uno strumento che consente di eseguire questa operazione, copiare prima di tutto la cartella dei dati dello strumento dalla libreria prima di eliminarla, quindi ripristinarla dopo la rigenerazione della libreria.
1. Riaprire il progetto in Unity
1. Importare i nuovi pacchetti Unity
    - Foundation: _importare prima questo pacchetto_
    - Strumenti
    - Opzionale Estensioni
    > [!NOTE]
    > Se sono state installate estensioni aggiuntive, potrebbe essere necessario importarle nuovamente.
    - Opzionale Esempi
1. Chiudere Unity ed eliminare la cartella **Library** (per prima cosa leggere la nota riportata di seguito). Questo passaggio è necessario per forzare Unity ad aggiornare il database asset e a riconciliare i profili personalizzati esistenti.
1. Avviare Unity e per ogni scena nel progetto
    - Eliminare **MixedRealityToolkit** e **MixedRealityPlayspace**, se presente, dalla gerarchia. Questa operazione eliminerà la fotocamera principale, ma verrà ricreata nel passaggio successivo. Se una qualsiasi proprietà della fotocamera principale è stata modificata manualmente, sarà necessario riapplicarla manualmente una volta creata la nuova fotocamera.
    - Selezionare **MixedRealityToolkit-> Aggiungi a scena e configura**
    - Selezionare **MixedRealityToolkit-> Utilities-> aggiornare-> i profili di mapping del controller** (necessario solo una volta). verranno aggiornati tutti i profili di mapping del controller personalizzato con assi e dati aggiornati, lasciando intatte le azioni di input personalizzate assegnate
1. Eseguire lo [strumento di migrazione](../features/tools/MigrationWindow.md) ed eseguire lo strumento nel *progetto completo* per assicurarsi che tutto il codice venga aggiornato alla versione più recente.
   La finestra migrazione contiene diversi gestori della migrazione, ognuno dei quali deve essere eseguito autonomamente. Questo passaggio include:
   - Selezionare il primo gestore della migrazione dall'elenco a discesa di **selezione del gestore della migrazione** .
   - Fare clic sul pulsante "progetto completo".
   - Fare clic sul pulsante "Aggiungi progetto completo per la migrazione". l'intero progetto verrà analizzato per la migrazione degli oggetti.
   - Fare clic sul pulsante "migrate", che deve essere abilitato se sono stati trovati oggetti migrabili.
   - Ripetere i tre passaggi precedenti per ogni gestore della migrazione all'interno dell'elenco a discesa.
     (Vedere [questo problema](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8552) che riguarda il lavoro che è possibile eseguire per semplificare questo processo di migrazione in una versione futura)

## <a name="updating-230-to-240"></a>Aggiornamento di 2.3.0 a 2.4.0

[Rinomina cartella](#folder-renames-in-240) 
 [Modifiche API](#api-changes-in-240)

### <a name="folder-renames-in-240"></a>Ridenominazione della cartella in 2.4.0

Le cartelle MixedRealityToolkit sono state rinominate e spostate in una gerarchia comune della versione 2,4. Se un'applicazione usa percorsi hardcoded per le risorse MRTK, sarà necessario aggiornarli in base alla tabella seguente.

| Cartella precedente | Nuova cartella |
| --- | --- |
| MixedRealityToolkit | MRTK/Core |
| MixedRealityToolkit. examples | MRTK/esempi |
| MixedRealityToolkit. Extensions | MRTK/estensioni |
| MixedRealityToolkit. Providers | MRTK/provider |
| MixedRealityToolkit. SDK | MRTK/SDK |
| MixedRealityToolkit. Services | MRTK/servizi |
| MixedRealityToolkit. test | MRTK/test |
| MixedRealityToolkit. Tools | MRTK/strumenti |

> [!IMPORTANT]
> `MixedRealityToolkit.Generated`Contiene i file generati dal cliente e rimane invariato.

### <a name="eye-gaze-setup-in-240"></a>Configurazione degli sguardi in 2.4.0

Questa versione di MRTK modifica i passaggi necessari per l'installazione di Eye sguardi. È possibile trovare la casella di controllo _' IsEyeTrackingEnabled '_ nelle impostazioni di sguardi del profilo puntatore di input. Se si seleziona questa casella, verrà abilitato lo sguardo basato sull'occhio, anziché lo sguardo predefinito basato sulla testa.

Per ulteriori informazioni su queste modifiche e istruzioni complete per la configurazione della verifica degli occhi, vedere l'articolo relativo alla [Verifica](../features/eye-tracking/EyeTracking_BasicSetup.md) degli occhi.

### <a name="eye-gaze-pointer-behavior-in-240"></a>Comportamento del puntatore a sguardi oculari in 2.4.0

Il comportamento dell'indicatore di misura predefinito per gli occhi è stato modificato in modo da corrispondere al comportamento predefinito del puntatore. Quando viene rilevata una mano, un puntatore a sguardi occhi verrà eliminato automaticamente. Il puntatore a sguardi occhi diventerà nuovamente visibile dopo aver detto "Select".

Per informazioni dettagliate sulle configurazioni dello sguardo e della mano, vedere l'articolo relativo [agli occhi e alle mani](../features/eye-tracking/EyeTracking_EyesAndHands.md#how-to-keep-gaze-pointer-always-on) .

### <a name="api-changes-in-240"></a>Modifiche alle API in 2.4.0

**Classi controller personalizzate**

Classi controller personalizzate in precedenza dovevano definire `SetupDefaultInteractions(Handedness)` . Questo metodo è stato reso obsoleto in 2,4, poiché il parametro di manualità era ridondante con la propria manualità della classe controller. Il nuovo metodo non dispone di parametri. Inoltre, molte classi controller hanno definito questo metodo nello stesso modo ( `AssignControllerMappings(DefaultInteractions);` ), quindi la chiamata completa è stata sottoposta a refactoring in ed è stato `BaseController` eseguito un override facoltativo anziché obbligatorio.

**Proprietà degli sguardi**

La `UseEyeTracking` proprietà dall' `GazeProvider` implementazione di `IMixedRealityEyeGazeProvider` è stata rinominata in `IsEyeTrackingEnabled` .

Se questa operazione è stata eseguita in precedenza...

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.UseEyeTracking = true;
}
```

Esegui ora...

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.IsEyeTrackingEnabled = true;
}
```

**Proprietà di WindowsApiChecker**

Le proprietà WindowsApiChecker seguenti sono state contrassegnate come obsolete. Usare `IsMethodAvailable` `IsPropertyAvailable` o `IsTypeAvailable` .

- UniversalApiContractV8_IsAvailable
- UniversalApiContractV7_IsAvailable
- UniversalApiContractV6_IsAvailable
- UniversalApiContractV5_IsAvailable
- UniversalApiContractV4_IsAvailable
- UniversalApiContractV3_IsAvailable

Non sono previsti piani per aggiungere proprietà a WindowsApiChecker per le versioni future del contratto API.

**GltfMeshPrimitiveAttributes di sola lettura**

Gli attributi primitivi mesh gltf usati per essere impostati, sono ora di sola lettura. I valori verranno impostati una volta quando vengono deserializzati.

### <a name="custom-button-icon-migration"></a>Icona del pulsante personalizzata migrazione

Nelle icone dei pulsanti personalizzate in precedenza è necessario assegnare un nuovo materiale al renderer quad del pulsante. Questa operazione non è più necessaria e si consiglia di trasferire le trame delle icone personalizzate in un. Vengono conservati i materiali e le icone personalizzati esistenti. Tuttavia, saranno meno ottimali fino a quando non vengono aggiornati.
Per aggiornare gli asset di tutti i pulsanti nel progetto al nuovo formato consigliato, usare ButtonConfigHelperMigrationHandler.
(Mixed Reality Toolkit-> Utilities-> finestra di migrazione > selezione del gestore della migrazione-> Microsoft. MixedReality. Toolkit. Utilities. ButtonConfigHelperMigrationHandler)

![Finestra di dialogo Aggiorna finestra](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

Se un'icona non viene trovata nel set di icone predefinito durante la migrazione, viene creato un set di icone personalizzato in MixedRealityToolkit. generated/CustomIconSets. Una finestra di dialogo indicherà che questa operazione è stata eseguita.

![Notifica dell'icona personalizzata](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

## <a name="updating-220-to-230"></a>Aggiornamento di 2.2.0 a 2.3.0

- [Modifiche all'API](#api-changes-in-230)

### <a name="api-changes-in-230"></a>Modifiche alle API in 2.3.0

**ControllerPoseSynchronizer**

Il campo ControllerPoseSynchronizer. manualità privato è stato contrassegnato come obsoleto. Questa operazione dovrebbe avere un effetto minimo sulle applicazioni perché il campo non è visibile all'esterno della relativa classe.

Il metodo di impostazione della proprietà ControllerPoseSynchronizer. manualità è stato rimosso ([#7012](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7012)).

**MSBuild per Unity**

Questa versione di MRTK usa una versione più recente di MSBuild per Unity rispetto alle versioni precedenti. Durante il caricamento del progetto, se la versione precedente è elencata nel manifesto di gestione pacchetti Unity, viene visualizzata la finestra di dialogo di configurazione con l'opzione Abilita MSBuild per Unity selezionata. L'applicazione eseguirà un aggiornamento.

**ScriptingUtilities**

La classe ScriptingUtilities è stata contrassegnata come obsoleta ed è stata sostituita da ScriptUtilities nell'assembly Microsoft. MixedReality. Toolkit. Editor. Utilities. La nuova classe perfeziona il comportamento precedente e aggiunge il supporto per la rimozione delle definizioni di scripting.

Mentre il codice esistente continuerà a funzionare nella versione 2.3.0, è consigliabile eseguire l'aggiornamento alla nuova classe.

**ShellHandRayPointer**

I membri lineRendererSelected e lineRendererNoTarget della classe ShellHandRayPointer sono stati sostituiti rispettivamente da lineMaterialSelected e lineMaterialNoTarget ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6863)).

Sostituire lineRendererSelected con lineMaterialSelected e/o lineRendererNoTarget con lineMaterialNoTarget per risolvere gli errori di compilazione.

**Startupbehavior facendo osservatore spaziale**

Gli osservatori spaziali basati sulla `BaseSpatialObserver` classe ora rispettano il valore di startupbehavior facendo quando viene riabilitato ([#6919](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6919)).

Non sono necessarie modifiche per sfruttare questa correzione.

**Prefabbricati del controllo UX aggiornati per l'uso di PressableButton**

I prefabbricati seguenti usano ora il componente PressableButton anziché TouchHandler per l'interazione near ([7070](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7070))

- AnimationButton
- Pulsante
- ButtonHoloLens1
- ButtonHoloLens1Toggle
- CheckBox
- RadialSet
- ToggleButton
- ToggleSwitch
- UnityUIButton
- UnityUICheckboxButton
- UnityUIRadialButton
- UnityUIToggleButton

Il codice dell'applicazione può richiedere l'aggiornamento a causa di questa modifica.

**Spazio dei nomi WindowsMixedRealityUtilities**

Lo spazio dei nomi di WindowsMixedRealityUtilities è stato modificato da Microsoft. MixedReality. Toolkit. WindowsMixedReality. input a Microsoft. MixedReality. Toolkit. WindowsMixedReality ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6989)).

Aggiornare #using le istruzioni per risolvere gli errori di compilazione.

## <a name="updating-210-to-220"></a>Aggiornamento di 2.1.0 a 2.2.0

- [Modifiche all'API](#api-changes-in-220)

### <a name="api-changes-in-220"></a>Modifiche alle API in 2.2.0

**IMixedRealityBoundarySystem. Contains**

Questo metodo ha eseguito in precedenza un'enumerazione sperimentale specifica definita da Unity. Ora accetta un'enumerazione definita da MRTK che è identica all'enumerazione Unity. Questa modifica consente di preparare il MRTK per le API limite future di Unity.

**MixedRealityServiceProfileAttribute**

Per descrivere meglio i requisiti per il supporto di un profilo, MixedRealityServiceProfileAttribute è stato aggiornato per aggiungere una raccolta facoltativa di tipi esclusi. Come parte di questa modifica, la proprietà ServiceType è stata modificata dal tipo al tipo [] ed è stata rinominata in RequiredTypes.

È stata aggiunta anche una seconda proprietà, ExcludedTypes.

## <a name="updating-200-to-210"></a>Aggiornamento di 2.0.0 a 2.1.0

- [Modifiche all'API](#api-changes-in-210)
- [Modifiche del profilo](#profile-changes-in-210)

### <a name="api-changes-in-210"></a>Modifiche alle API in 2.1.0

**BaseNearInteractionTouchable**

`BaseNearInteractionTouchable`È stato modificato per contrassegnare il `OnValidate` metodo come virtuale. Le classi che estendono, `BaseNearInteractionTouchable` `NearInteractionTouchableUnityUI` ad esempio, sono state aggiornate per riflettere questa modifica.

**ColliderNearInteractionTouchable**

La classe `ColliderNearInteractionTouchable` è stata deprecata. Aggiornare i riferimenti al codice da usare `BaseNearInteractionTouchable` .

**IMixedRealityMouseDeviceManager**

**_Aggiunto_**

`IMixedRealityMouseDeviceManager` sono state aggiunte `CursorSpeed` le `WheelSpeed` proprietà e. Queste proprietà consentono alle applicazioni di specificare un valore moltiplicatore in base al quale verrà ridimensionata rispettivamente la velocità del cursore e della rotellina.

Si tratta di una modifica sostanziale che richiede la modifica delle implementazioni di gestione dispositivi del mouse esistenti.

>[!NOTE]
>Questa modifica non è compatibile con le versioni precedenti della versione 2.0.0.

**_Deprecato_**

La `MouseInputProfile` proprietà è stata contrassegnata come obsoleta e verrà rimossa da una versione futura di Microsoft Mixed Reality Toolkit. Si consiglia di non usare più questa proprietà per il codice dell'applicazione.

**Con cui**

I metodi e le proprietà seguenti sono stati deprecati e verranno rimossi da una versione futura di Microsoft Mixed Reality Toolkit. È consigliabile aggiornare il codice dell'applicazione in base alle linee guida contenute nell'attributo obsolete e visualizzarle nella console di.

- `public bool Enabled`
- `public bool FocusEnabled`
- `public void ForceUpdateThemes()`
- `public bool IsDisabled`
- `public bool IsToggleButton`
- `public int GetDimensionIndex()`
- `public State[] GetStates()`
- `public bool RequiresFocus`
- `public void ResetBaseStates()`
- `public virtual void SetCollision(bool collision)`
- `public virtual void SetCustom(bool custom)`
- `public void SetDimensionIndex(int index)`
- `public virtual void SetDisabled(bool disabled)`
- `public virtual void SetFocus(bool focus)`
- `public virtual void SetGesture(bool gesture)`
- `public virtual void SetGestureMax(bool gesture)`
- `public virtual void SetGrab(bool grab)`
- `public virtual void SetInteractive(bool interactive)`
- `public virtual void SetObservation(bool observation)`
- `public virtual void SetObservationTargeted(bool targeted)`
- `public virtual void SetPhysicalTouch(bool touch)`
- `public virtual void SetPress(bool press)`
- `public virtual void SetTargeted(bool targeted)`
- `public virtual void SetToggled(bool toggled)`
- `public virtual void SetVisited(bool visited)`
- `public virtual void SetVoiceCommand(bool voice)`

**NearInteractionTouchableSurface**

La `NearInteractionTouchableSurface` classe è stata aggiunta e ora funge da classe di base per `NearInteractionTouchable` e `NearInteractionTouchableUnityUI` .

### <a name="profile-changes-in-210"></a>Modifiche del profilo in 2.1.0

**Profilo di rilevamento mano**

La mesh mano e le visualizzazioni congiunte dispongono ora di impostazioni distinte per l'editor e il lettore. Il profilo di rilevamento della mano è stato aggiornato per consentire l'impostazione di queste visualizzazioni su; Niente, tutto, editor o lettore.

![Modalità di visualizzazione mano](../features/images/release-notes/HandTrackingVisualizationModes.png)

Potrebbe essere necessario aggiornare i profili di rilevamento mano personalizzati per funzionare correttamente con la versione 2.1.0.

>[!NOTE]
>Questa modifica non è compatibile con le versioni precedenti della versione 2.0.0.

**Profilo simulazione di input**

Il sistema di simulazione di input è stato aggiornato, che consente di modificare alcune impostazioni nel profilo di simulazione di input. Non è possibile eseguire la migrazione automatica di alcune modifiche e gli utenti potrebbero rilevare che i profili utilizzano valori predefiniti.

1. Tutti i binding dei pulsanti del mouse e del KeyCode nel profilo sono stati sostituiti con uno `KeyBinding` struct generico, che archivia il tipo di binding (chiave o mouse), nonché il codice di associazione effettivo (rispettivamente, il numero di tasto del mouse o il prefisso). Lo struct dispone di un proprio controllo, che consente la visualizzazione unificata e offre uno strumento di associazione automatica per impostare rapidamente le combinazioni di tasti premendo la rispettiva chiave invece di selezionare da un elenco a discesa di grandi dimensioni.

    - FastControlKey
    - ToggleLeftHandKey
    - ToggleRightHandKey
    - LeftHandManipulationKey
    - RightHandManipulationKey

1. `MouseLookToggle` in precedenza era incluso nell' `MouseLookButton` enum come `InputSimulationMouseButton.Focused` , ora è un'opzione separata. Se abilitata, la fotocamera continuerà a ruotare con il mouse dopo aver rilasciato il pulsante, fino a quando non viene premuto il tasto di escape.
1. `HandDepthMultiplier` il valore predefinito è stato abbassato da 0,1 a 0,03 per adattare alcune modifiche alla simulazione di input. Se lo scorrimento della fotocamera si sposta troppo rapidamente, provare a ridurre questo valore.
1. Le chiavi per la rotazione delle mani sono state rimosse. la rotazione della mano è ora controllata anche dal mouse. Tenendo premuto `HandRotateButton` (CTRL) insieme alla chiave di manipolazione a sinistra/destra (LShift/spazio), viene abilitata la rotazione della mano.
1. È stato introdotto un nuovo asse "UpDown" nell'elenco degli assi di input. Questo controlla lo spostamento della fotocamera in verticale e il valore predefinito per le chiavi Q/E, nonché i pulsanti del trigger del controller.

Per ulteriori informazioni su queste modifiche, vedere l'articolo relativo al [servizio di simulazione input](../features/input-simulation/InputSimulationService.md) .

**Profilo provider di dati del mouse**

Il profilo del provider di dati del mouse è stato aggiornato per esporre le nuove `CursorSpeed` `WheelSpeed` proprietà e. Ai profili personalizzati esistenti verranno automaticamente specificati i valori predefiniti. Quando il profilo viene salvato, questi nuovi valori saranno resi permanente.

**Profilo di mapping del controller**

Alcuni assi e tipi di input sono stati aggiornati in 2.1.0, in particolare per la piattaforma OpenVR. Quando si esegue l'aggiornamento, assicurarsi di selezionare **MixedRealityToolkit-> Utilities-> i profili di mapping del controller di aggiornamento->** . In questo caso i profili di mapping del controller personalizzato vengono aggiornati con gli assi e i dati aggiornati, lasciando intatti le azioni di input personalizzate.

## <a name="updating-rc2-to-200"></a>Aggiornamento RC2 alla 2.0.0

Tra le versioni RC2 e 2.0.0 del Toolkit Microsoft Mixed Reality, sono state apportate modifiche che potrebbero influito sui progetti esistenti. Questo documento descrive le modifiche e come aggiornare i progetti alla versione 2.0.0.

- [Modifiche all'API](#api-changes-in-200)
- [Modifiche al nome dell'assembly](#assembly-name-changes-in-200)

### <a name="api-changes-in-200"></a>Modifiche alle API nella 2.0.0

Dalla versione RC2 sono state apportate alcune modifiche alle API, incluse alcune che potrebbero comportare interruzioni dei progetti esistenti. Le sezioni seguenti descrivono le modifiche che si sono verificate tra le versioni RC2 e 2.0.0.

**MixedRealityToolkit**

Le seguenti proprietà pubbliche nell'oggetto MixedRealityToolkit sono state deprecate.

- `RegisteredMixedRealityServices` non contiene più la raccolta di servizi e provider di dati delle estensioni registrate.

Per accedere ai servizi di estensione, utilizzare `MixedRealityServiceRegistry.TryGetService<T>` . Per accedere ai provider di dati, eseguire il cast dell'istanza del servizio a [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) e utilizzare `GetDataProvider<T>` .

Utilizzare [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) o [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) invece per le seguenti proprietà deprecate

- `ActiveSystems`
- `InputSystem`
- `BoundarySystem`
- `CameraSystem`
- `SpatialAwarenessSystem`
- `TeleportSystem`
- `DiagnosticsSystem`
- `SceneSystem`

**CoreServices**

La [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) classe è la sostituzione per le funzioni di accesso di sistema statiche (ad esempio, BoundarySystem) trovate nell' `MixedRealityToolkit` oggetto.

>[!IMPORTANT]
>Le `MixedRealityToolkit` funzioni di accesso di sistema sono state deprecate nella versione 2.0.0 e verranno rimosse in una versione futura di MRTK.

Nell'esempio di codice seguente vengono illustrati il vecchio e il nuovo modello.

``` c#
// Old
GameObject playAreaVisualization = MixedRealityToolkit.BoundarySystem?.GetPlayAreaVisualization();

// New
GameObject playAreaVisualization = CoreServices.BoundarySystem?.GetPlayAreaVisualization();
```

Se si utilizza la nuova classe CoreSystem, il codice dell'applicazione non richiederà l'aggiornamento se si modifica l'applicazione per l'utilizzo di un registrar del servizio diverso (ad esempio, uno dei responsabili del servizio sperimentale).

**IMixedRealityRaycastProvider**

Con l'aggiunta di IMixedRealityRaycastProvider, il profilo di configurazione del sistema di input è stato modificato. Se si dispone di un profilo personalizzato, è possibile che vengano visualizzati gli errori nell'immagine seguente quando si esegue l'applicazione.

![Selezione dei dettagli dell'errore del provider Raycast](../features/images/release-notes/UnableToRegisterRaycastProvider.png)

Per risolvere il problema, aggiungere un'istanza di IMixedRealityRaycastProvider al profilo di sistema di input.

![Selezione del provider Raycast](../features/images/release-notes/SelectRaycastProvider.png)

**Sistema di eventi**

- I `IMixedRealityEventSystem` metodi dell'API obsoleti `Register` e `Unregister` sono stati contrassegnati come obsoleti. Sono conservati per la compatibilità con le versioni precedenti.
- `InputSystemGlobalListener` è stato contrassegnato come obsoleto. La relativa funzionalità non è stata modificata.
- `BaseInputHandler` la classe base è stata modificata da `InputSystemGlobalListener` a `InputSystemGlobalHandlerListener` . Si tratta di una modifica di rilievo per qualsiasi discendente di `BaseInputHandler` .

**_Motivazione alla base della modifica_**

L'API del sistema di eventi precedente `Register` e `Unregister` potrebbe causare più problemi in fase di esecuzione, Main:

- Se un componente si registra per gli eventi globali, riceverà gli eventi di input globali di *tutti i* tipi.
- Se uno dei componenti di un oggetto viene registrato per gli eventi di input globali, tutti i componenti di questo oggetto riceveranno gli eventi di input globali di *tutti i* tipi.
- Se due componenti sullo stesso oggetto si registrano in eventi globali e uno è disabilitato in fase di esecuzione, il secondo arresta la ricezione di eventi globali.

Nuova API `RegisterHandler` e `UnregisterHandler` :

- Fornisce un controllo esplicito e granulare su quali eventi di input devono essere ascoltati a livello globale e che devono essere basati su uno stato attivo.
- Consente a più componenti sullo stesso oggetto di restare in ascolto di eventi globali in modo indipendente l'uno dall'altro.

**_Come eseguire la migrazione_**

- Se è stata chiamata l' `Register` / `Unregister` API direttamente prima, sostituire queste chiamate con le chiamate a `RegisterHandler` / `UnregisterHandler` . Usare le interfacce del gestore implementate come parametri generici. Se si implementano più interfacce e molte di esse sono in ascolto di eventi di input globali, chiamare `RegisterHandler` più volte.
- Se è stata ereditata da `InputSystemGlobalListener` , modificare l'ereditarietà in `InputSystemGlobalHandlerListener` . Implementano `RegisterHandlers` `UnregisterHandlers` metodi astratti e. Nella chiamata di implementazione `inputSystem.RegisterHandler` ( `inputSystem.UnregisterHandler` ) per eseguire la registrazione in tutte le interfacce del gestore per cui si desidera ascoltare gli eventi globali.
- Se è stata ereditata da `BaseInputHandler` , implementare `RegisterHandlers` e i `UnregisterHandlers` metodi astratti (come per `InputSystemGlobalListener` ).

**_Esempi di migrazione_**

```c#
// Old
class SampleHandler : MonoBehaviour, IMixedRealitySourceStateHandler, IMixedRealityHandJointHandler
{
    private void OnEnable()
    {
        InputSystem?.Register(gameObject);
    }

    private void OnDisable()
    {
        InputSystem?.Unregister(gameObject);
    }
}

// Migrated
class SampleHandler : MonoBehaviour, IMixedRealitySourceStateHandler, IMixedRealityHandJointHandler
{
    private void OnEnable()
    {
        InputSystem?.RegisterHandler<IMixedRealitySourceStateHandler>(this);
        InputSystem?.RegisterHandler<IMixedRealityHandJointHandler>(this);
    }

    private void OnDisable()
    {
        InputSystem?.UnregisterHandler<IMixedRealitySourceStateHandler>(this);
        InputSystem?.UnregisterHandler<IMixedRealityHandJointHandler>(this);
    }
}
```

```c#
// Old
class SampleHandler2 : InputSystemGlobalListener, IMixedRealitySpeechHandler
{
}

// Migrated
class SampleHandler2 : InputSystemGlobalHandlerListener, IMixedRealitySpeechHandler
{
    private void RegisterHandlers()
    {
        InputSystem?.RegisterHandler<IMixedRealitySpeechHandler>(this);
    }

    private void UnregisterHandlers()
    {
        InputSystem?.UnregisterHandler<IMixedRealitySpeechHandler>(this);
    }
}

// Alternative migration
class SampleHandler2 : MonoBehaviour, IMixedRealitySpeechHandler
{
    private void OnEnable()
    {
        IMixedRealityInputSystem inputSystem;
        if (MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
        {
            inputSystem?.RegisterHandler<IMixedRealitySpeechHandler>(this);
        }
    }

    private void OnDisable()
    {
        IMixedRealityInputSystem inputSystem;
        if (MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
        {
            inputSystem?.UnregisterHandler<IMixedRealitySpeechHandler>(this);
        }
    }
}
```

**Consapevolezza spaziale**

Per le interfacce IMixedRealitySpatialAwarenessSystem e IMixedRealitySpatialAwarenessObserver sono state apportate più modifiche di rilievo, come descritto di seguito.

**_Modifiche_**

I metodi seguenti sono stati rinominati per descrivere meglio l'utilizzo.

- `IMixedRealitySpatialAwarenessSystem.CreateSpatialObjectParent` è stato rinominato in `IMixedRealitySpatialAwarenessSystem.CreateSpatialAwarenessObservationParent` per chiarirne l'utilizzo.

**_Aggiornamenti_**

In base ai commenti e suggerimenti dei clienti, è stato aggiunto il supporto per semplificare la rimozione di dati di consapevolezza spaziale osservati in precedenza.

- `IMixedRealitySpatialAwarenessSystem.ClearObservations()`
- `IMixedRealitySpatialAwarenessSystem.ClearObservations<T>(string name)`
- `IMixedRealitySpatialAwarenessObserver.ClearObservations()`

**Risolutori**

Alcuni componenti del Risolutore e la classe SolverHandler Manager sono stati modificati per correggere diversi bug e per un utilizzo più intuitivo.

**_SolverHandler_**

- La classe non si estende più da `ControllerFinder`
- `TrackedObjectToReference` Proprietà pubblica deprecata ed è stata rinominata in `TrackedTargetType`
- `TrackedObjectType` depreca i valori Left & right controller. Usare invece `MotionController` `HandJoint` i valori o e aggiornare la nuova `TrackedHandedness` proprietà per limitare il rilevamento al controller sinistro o destro

**_InBetween_**

- `TrackedObjectForSecondTransform` Proprietà pubblica deprecata ed è stata rinominata in `SecondTrackedObjectType`
- `AttachSecondTransformToNewTrackedObject()` è stato rimosso. Per aggiornare il Risolutore, modificare le proprietà pubbliche, ad esempio `SecondTrackedObjectType`)

**_SurfaceMagnetism_**

- `MaxDistance` Proprietà pubblica deprecata ed è stata rinominata in `MaxRaycastDistance`
- `CloseDistance` Proprietà pubblica deprecata ed è stata rinominata in `ClosestDistance`
- Il valore predefinito per `RaycastDirectionMode` è ora `TrackedTargetForward` raycasts nella direzione della trasformazione di destinazione rilevata in avanti.
- `OrientationMode`i valori enum, `Vertical` e `Full` , sono stati rinominati `TrackedTarget` rispettivamente in e `SurfaceNormal`
- `KeepOrientationVertical` è stata aggiunta la proprietà Public per controllare se l'orientamento del GameObject associato rimanga verticale

**Pulsanti**

- [`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton)`DistanceSpaceMode`la proprietà è ora impostata su `Local` come valore predefinito. In questo modo è possibile ridimensionare i pulsanti mentre sono ancora stampabili

**Sfera di ritaglio**

L'interfaccia ClippingSphere è cambiata per eseguire il mirroring delle API trovate in ClippingBox e ClippingPlane.

La proprietà RADIUS di ClippingSphere viene ora calcolata in modo implicito in base alla scala di trasformazione. Prima che gli sviluppatori dovessero specificare il raggio di ClippingSphere nel controllo. Se si vuole modificare il raggio, è sufficiente aggiornare la scala di trasformazione della trasformazione come si farebbe normalmente.

**NearInteractionTouchable e PokePointer**

- NearInteractionTouchable non gestisce più l'area di disegno dell'interfaccia utente di Unity. È necessario usare la classe NearInteractionTouchableUnityUI per l'interfaccia utente di Unity touchables Now.
- ColliderNearInteractionTouchable è la nuova classe di base per touchables in base ai Collider, ovvero ogni oggetto toccabile, ad eccezione di NearInteractionTouchableUnityUI.
- BaseNearInteractionTouchable. DistFront è stato spostato e rinominato in PokePointer. TouchableDistance è la distanza e la PokePointer può interagire con touchables. In precedenza ogni modificabile presentava una distanza di interazione massima, ma ora è definita in PokePointer, che consente una migliore ottimizzazione.
- BaseNearInteractionTouchable. DistBack è stato rinominato in PokeThreshold in modo da rendere chiaro che PokeThreshold è la controparte di DebounceThreshold. Un oggetto toccabile viene attivato quando viene superato il valore di PokeThreshold e viene rilasciato quando DebounceThreshold viene attraversato.

**ReadOnlyAttribute**

Lo `Microsoft.MixedReality.Toolkit` spazio dei nomi è stato aggiunto a `ReadOnlyAttribute` , `BeginReadOnlyGroupAttribute` e `EndReadOnlyGroupAttribute` .

**PointerClickHandler**

La classe `PointerClickHandler` è stata deprecata. `PointerHandler`È invece necessario utilizzare l'oggetto, che fornisce la stessa funzionalità.

**Supporto di HoloLens Clicker**

I mapping del controller del clicker HoloLens sono passati a un valore non gestito [`WindowsMixedRealityController`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityController) [`WindowsMixedRealityGGVHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityGGVHand) . Per tenere conto di questo problema, viene eseguito un aggiornamento automatico la prima volta che si apre il profilo ControllerMapping. Aprire i profili personalizzati almeno una volta dopo l'aggiornamento a 2.0.0 per attivare questo passaggio di migrazione una volta.

**InteractableHighlight**

La classe `InteractableHighlight` è stata deprecata. In `InteractableOnFocus` alternativa, `FocusInteractableStates` è consigliabile usare la classe e l'asset. Per creare un nuovo `Theme` asset per il `InteractableOnFocus` , fare clic con il pulsante destro del mouse nella finestra del progetto e scegliere *Crea*  >    >  *tema interagibile* del Toolkit di realtà mista  >  .

**HandInteractionPanZoom**

`HandInteractionPanZoom` è stato spostato nello spazio dei nomi dell'interfaccia utente perché non era un componente di input. `HandPanEventData` è stato inoltre spostato in questo spazio dei nomi e semplificato per corrispondere ad altri dati degli eventi dell'interfaccia utente.

### <a name="assembly-name-changes-in-200"></a>Modifiche al nome dell'assembly in 2.0.0

Nella versione 2.0.0, tutti i nomi di assembly ufficiali del Toolkit di realtà mista e i file di definizione di assembly (con estensione asmdef) associati sono stati aggiornati per adattarsi al modello seguente.

```c#
Microsoft.MixedReality.Toolkit[.<name>]
```

In alcuni casi, sono Stati Uniti più assembly per creare una migliore Unity del rispettivo contenuto. Se il progetto usa file con estensione asmdef personalizzati, potrebbe essere necessario aggiornare.

Le tabelle seguenti descrivono il mapping dei nomi di file RC2. asmdef alla versione 2.0.0. Tutti i nomi di assembly corrispondono al nome del file. asmdef.

**MixedRealityToolkit**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit.asmdef | Microsoft. MixedReality. Toolkit. asmdef |
| MixedRealityToolkit. Core. BuildAndDeploy. asmdef | Microsoft. MixedReality. Toolkit. Editor. BuildAndDeploy. asmdef |
| MixedRealityToolkit. Core. Definitions. Utilities. Editor. asmdef | Rimosso, usare Microsoft. MixedReality. Toolkit. Editor. Utilities. asmdef |
| MixedRealityToolkit. Core. Extensions. EditorClassExtensions. asmdef | Microsoft. MixedReality. Toolkit. Editor. ClassExtensions. asmdef
| MixedRealityToolkit. Core. Inspectors. asmdef | Microsoft. MixedReality. Toolkit. Editor. Inspectors. asmdef |
| MixedRealityToolkit. Core. Inspectors. ServiceInspectors. asmdef | Microsoft. MixedReality. Toolkit. Editor. ServiceInspectors. asmdef |
| MixedRealityToolkit. Core. UtilitiesAsync. asmdef | Microsoft. MixedReality. Toolkit. Async. asmdef |
| MixedRealityToolkit. Core. Utilities. Editor. asmdef | Microsoft. MixedReality. Toolkit. Editor. Utilities. asmdef |
| MixedRealityToolkit. Utilities. Gltf. asmdef | Microsoft. MixedReality. Toolkit. Gltf. asmdef |
| MixedRealityToolkit. Utilities. Gltf. Importers. asmdef | Microsoft. MixedReality. Toolkit. Gltf. Importers. asmdef |

**MixedRealityToolkit. Providers**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit. Providers. OpenVR. asmdef | Microsoft. MixedReality. Toolkit. Providers. OpenVR. asmdef |
| MixedRealityToolkit. Providers. WindowsMixedReality. asmdef | Microsoft. MixedReality. Toolkit. Providers. WindowsMixedReality. asmdef |
| MixedRealityToolkit. Providers. WindowsVoiceInput. asmdef | Microsoft. MixedReality. Toolkit. Providers. WindowsVoiceInput. asmdef |

**MixedRealityToolkit. Services**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit. Services. BoundarySystem. asmdef | Microsoft. MixedReality. Toolkit. Services. BoundarySystem. asmdef |
| MixedRealityToolkit. Services. CameraSystem. asmdef | Microsoft. MixedReality. Toolkit. Services. CameraSystem. asmdef |
| MixedRealityToolkit. Services. DiagnosticsSystem. asmdef | Microsoft. MixedReality. Toolkit. Services. DiagnosticsSystem. asmdef |
| MixedRealityToolkit. Services. InputSimulation. asmdef | Microsoft. MixedReality. Toolkit. Services. InputSimulation. asmdef |
| MixedRealityToolkit. Services. InputSimulation. Editor. asmdef | Microsoft. MixedReality. Toolkit. Services. InputSimulation. Editor. asmdef |
| MixedRealityToolkit. Services. InputSystem. asmdef | Microsoft. MixedReality. Toolkit. Services. InputSystem. asmdef |
| MixedRealityToolkit. Services. Inspectors. asmdef | Microsoft. MixedReality. Toolkit. Services. InputSystem. Editor. asmdef |
| MixedRealityToolkit. Services. SceneSystem. asmdef | Microsoft. MixedReality. Toolkit. Services. SceneSystem. asmdef |
| MixedRealityToolkit. Services. SpatialAwarenessSystem. asmdef | Microsoft. MixedReality. Toolkit. Services. SpatialAwarenessSystem. asmdef |
| MixedRealityToolkit. Services. TeleportSystem. asmdef | Microsoft. MixedReality. Toolkit. Services. TeleportSystem. asmdef |

**MixedRealityToolkit. SDK**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit. SDK. asmdef | Microsoft. MixedReality. Toolkit. SDK. asmdef |
| MixedRealityToolkit. SDK. Inspectors. asmdef | Microsoft. MixedReality. Toolkit. SDK. Inspectors. asmdef |

**MixedRealityToolkit. examples**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit. examples. asmdef | Microsoft. MixedReality. Toolkit. examples. asmdef |
| MixedRealityToolkit. examples. Demos. Gltf. asmdef | Microsoft. MixedReality. Toolkit. Demos. Gltf. asmdef |
| MixedRealityToolkit. examples. Demos. StandardShader. Inspectors. asmdef | Microsoft. MixedReality. Toolkit. Demos. StandardShader. Inspectors. asmdef |
| MixedRealityToolkit. examples. Demos. Utilities. InspectorFields. asmdef | Microsoft. MixedReality. Toolkit. Demos. InspectorFields. asmdef |
| MixedRealityToolkit. examples. Demos. Utilities. InspectorFields. Inspectors. asmdef | Microsoft. MixedReality. Toolkit. Demos. InspectorFields. Inspectors. asmdef |
| MixedRealityToolkit. examples. Demos. UX. Interactables. asmdef | Microsoft. MixedReality. Toolkit. Demos. UX. Interactables. asmdef |
