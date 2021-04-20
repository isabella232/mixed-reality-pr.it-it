---
title: Aggiornamento
description: Documentazione per eseguire la migrazione da una versione precedente di MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 04/19/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 97f45328bc8f9b811e815da0240138790db699c6
ms.sourcegitcommit: 0b09536c16f6802acc120a973d720aec7e30f617
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2021
ms.locfileid: "107742237"
---
# <a name="updating-the-microsoft-mixed-reality-toolkit"></a>Aggiornamento di Microsoft Mixed Reality Toolkit

- [Aggiornamento a una nuova versione di MRTK](#upgrading-to-a-new-version-of-mrtk)
- [Da 2.3.0 a 2.4.0](#updating-230-to-240)
- [Da 2.2.0 a 2.3.0](#updating-220-to-230)
- [Da 2.1.0 a 2.2.0](#updating-210-to-220)
- [Da 2.0.0 a 2.1.0](#updating-200-to-210)
- [Da RC2 a 2.0.0](#updating-rc2-to-200)

## <a name="finding-the-current-version"></a>Ricerca della versione corrente 

Seguire queste istruzioni per determinare la versione di MRTK attualmente in uso:

1. Aprire il progetto MRTK in Unity
2. Passare alla cartella "MixedRealityToolkit" nella finestra del progetto
3. Aprire il file denominato "Version"

Se il file e la cartella precedenti non esistono, si è in una versione più recente di MRTK. In tal caso, provare a eseguire le operazioni seguenti:

1. Passare alla cartella "Mixed Reality Toolkit Foundation"
2. Fare clic sul pulsante "package.js" per visualizzare un'anteprima in Unity o aprirlo con un editor di testo
3. Cercare la riga con la parola "version:" 

## <a name="upgrading-to-a-new-version-of-mrtk"></a>Aggiornamento a una nuova versione di MRTK

*È consigliabile eseguire [](../features/tools/migration-window.md) lo* strumento di migrazione dopo aver eseguito l'aggiornamento MRTK per la correzione automatica e l'aggiornamento da componenti deprecati e dopo aver apportato modifiche di rilievo. Lo strumento di migrazione fa parte del **pacchetto** Tools.

Le istruzioni seguenti descrivono il percorso di aggiornamento da 2.4.0 a 2.5.0. Se il progetto è nella versione 2.3.0 [](#updating-230-to-240) o precedente, leggere le modifiche tra [](https://microsoft.github.io/MixedRealityToolkit-Unity/version/releases/2.4.0/Documentation/Updating.html) le versioni per comprendere il percorso di aggiornamento o leggere le istruzioni della versione precedente per eseguire un aggiornamento versione per versione.

### <a name="mixed-reality-feature-tool"></a>Strumento per la funzionalità di realtà mista
Il modo più semplice per aggiornare MRTK a una versione più recente di MRTK è usare [mixed reality feature tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) per scaricare i pacchetti più recenti e caricarli direttamente nel progetto Unity.

Se il progetto usava in precedenza file di asset Unity (con estensione unitypackage), vedere [queste istruzioni.](#switching-from-unity-asset-files-to-mixed-reality-feature-tool) 

### <a name="unity-asset-unitypackage-files"></a>File di asset Unity (con estensione unitypackage)

Un altro percorso di aggiornamento è scaricare manualmente i pacchetti DIRTK Unity e applicarli al progetto. Vedere la procedura seguente,

1. Salvare una copia del progetto corrente, nel caso in cui si sbatta in qualsiasi punto della procedura di aggiornamento.
1. Chiudere Unity
1. *All'interno della cartella Assets* eliminare le cartelle **MRTK** seguenti, insieme ai relativi file con estensione meta (il progetto potrebbe non avere tutte le cartelle elencate)
    - MRTK/Core
    - MRTK/Esempi
    - MRTK/Extensions
    - MRTK/Providers
    - MRTK/SDK
    - MRTK/Services
    - MRTK/StandardAssets
    > [!IMPORTANT]
    > Se sono state apportate modifiche agli shader MRTK, creare un backup locale prima di eliminare la cartella MRTK/StandardAssets
    - MRTK/Strumenti
    > [!IMPORTANT]
    > NON eliminare la **cartella MixedRealityToolkit.Generated** o il relativo file con estensione meta.
1. Eliminare la **cartella** Library
    > [!IMPORTANT]
    > Alcuni strumenti unity, ad esempio Unity Collab, salvano le informazioni di configurazione nella cartella Library. Se si usa uno strumento che esegue questa operazione, copiare prima di eliminare la cartella dati dello strumento dalla libreria, quindi ripristinarla dopo la rigenerazione della libreria.
1. Aprire nuovamente il progetto in Unity
1. Importare i nuovi pacchetti Unity
    - Foundation- _Importare prima questo pacchetto_
    - Strumenti
    - (Facoltativo) Estensioni
    > [!NOTE]
    > Se sono state installate estensioni aggiuntive, potrebbe essere necessario importare nuovamente tali estensioni.
    - (Facoltativo) Esempi
1. Chiudere Unity ed eliminare la **cartella Library** (leggere prima la nota seguente). Questo passaggio è necessario per forzare Unity ad aggiornare il database degli asset e riconciliare i profili personalizzati esistenti.
1. Avviare Unity e per ogni scena nel progetto
    - Eliminare **MixedRealityToolkit** e **MixedRealityPlayspace,** se presenti, dalla gerarchia. Questa operazione eliminerà la fotocamera principale, ma verrà ri-creata nel passaggio successivo. Se le proprietà della fotocamera principale sono state modificate manualmente, sarà necessario applicarne di nuovo manualmente una volta creata la nuova fotocamera.
    - Selezionare **MixedRealityToolkit -> Aggiungi alla scena e configura**
    - Selezionare **MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles** (Profili di mapping del controller di >- Questa operazione deve essere eseguita una sola volta) - In questo modo tutti i profili di mapping dei controller personalizzati verranno aggiornati con gli assi e i dati aggiornati, lasciando intatte le azioni di input assegnate dall'utente
1. Eseguire lo [strumento di migrazione](../features/tools/migration-window.md) ed eseguire lo strumento nel progetto *completo* per assicurarsi che tutto il codice sia aggiornato alla versione più recente.
   La finestra di migrazione contiene diversi gestori di migrazione, ognuno dei quali deve essere eseguito per conto proprio. Questo passaggio comporta:
   - Selezionare il primo gestore di migrazione dall'elenco **a discesa Selezione gestore** migrazione.
   - Fare clic sul pulsante "Progetto completo".
   - Fare clic sul pulsante "Aggiungi progetto completo per la migrazione" per analizzare l'intero progetto per trovare gli oggetti di cui eseguire la migrazione.
   - Fare clic sul pulsante "Migrate" (Esegui migrazione) che deve essere abilitato se sono stati trovati oggetti di cui è possibile eseguire la migrazione.
   - Ripetere i tre passaggi precedenti per ognuno dei gestori di migrazione nell'elenco a discesa.
     Vedere questo [problema che](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8552) illustra le operazioni che è possibile eseguire per semplificare questo processo di migrazione in una versione futura.

### <a name="switching-from-unity-asset-files-to-mixed-reality-feature-tool"></a>Passaggio dai file di asset di Unity a Mixed Reality Feature Tool

Il passaggio dai file di asset unity ai pacchetti dello strumento di funzionalità di realtà mista offre una serie di vantaggi:

- Aggiornamento più semplice
- Tempi di compilazione più rapidi
- Meno progetti nella soluzione Visual Studio

Il passaggio all'uso di Mixed Reality Feature Tool richiede un set di passaggi manuali una sola volta.

1. Salvare una copia del progetto corrente.
1. Chiudere Unity
1. *All'interno della cartella Assets* eliminare le cartelle **MRTK** seguenti, insieme ai relativi file con estensione meta (il progetto potrebbe non avere tutte le cartelle elencate)
    - MRTK/Core
    - MRTK/Esempi
    - MRTK/Extensions
    - MRTK/Providers
    - MRTK/SDK
    - MRTK/Services
    - MRTK/StandardAssets
    > [!IMPORTANT]
    > Se sono state apportate modifiche agli shader MRTK, creare un backup locale prima di eliminare la cartella MRTK/StandardAssets
    - MRTK/Strumenti
    > [!IMPORTANT]
    > NON eliminare la **cartella MixedRealityToolkit.Generated** o il relativo file con estensione meta.
1. Eliminare la **cartella** Library
    > [!IMPORTANT]
    > Alcuni strumenti unity, ad esempio Unity Collab, salvano le informazioni di configurazione nella cartella Library. Se si usa uno strumento che esegue questa operazione, copiare prima di eliminare la cartella dei dati dello strumento dalla libreria, quindi ripristinarla dopo la rigenerazione della libreria.
1. Aprire nuovamente il progetto in Unity

Dopo aver eseguito i passaggi precedenti, esegui [Mixed Reality Feature Tool](#mixed-reality-feature-tool) e importa la versione desiderata di Mixed Reality Toolkit.

## <a name="updating-230-to-240"></a>Aggiornamento dalla versione 2.3.0 alla versione 2.4.0

[Ridenominazione delle cartelle](#folder-renames-in-240) 
 [Modifiche all'API](#api-changes-in-240)

### <a name="folder-renames-in-240"></a>Ridenominazione delle cartelle nella versione 2.4.0

Le cartelle MixedRealityToolkit sono state rinominate e spostate in una gerarchia comune nella versione 2.4. Se un'applicazione usa percorsi hard coded per le risorse MRTK, dovrà essere aggiornata in base alla tabella seguente.

| Cartella precedente | Nuova cartella |
| --- | --- |
| MixedRealityToolkit | MRTK/Core |
| MixedRealityToolkit.Examples | MRTK/Esempi |
| MixedRealityToolkit.Extensions | MRTK/Extensions |
| MixedRealityToolkit.Providers | MRTK/Providers |
| MixedRealityToolkit.SDK | MRTK/SDK |
| MixedRealityToolkit.Services | MRTK/Services |
| MixedRealityToolkit.Tests | MRTK/Tests |
| MixedRealityToolkit.Tools | MRTK/Tools |

> [!IMPORTANT]
> Contiene `MixedRealityToolkit.Generated` i file generati dal cliente e rimane invariato.

### <a name="eye-gaze-setup-in-240"></a>Configurazione dello sguardo fisso nella versione 2.4.0

Questa versione di MRTK modifica i passaggi necessari per la configurazione dello sguardo fisso. La _casella di controllo "IsEyeTrackingEnabled"_ è disponibile nelle impostazioni dello sguardo del profilo puntatore di input. Se si seleziona questa casella, lo sguardo basato sull'occhio verrà abilitato, anziché lo sguardo predefinito basato sulla testa.

Per altre informazioni su queste modifiche e istruzioni complete per la configurazione del tracciamento oculare, vedere l'articolo [sul tracciamento](../features/input/eye-tracking/eye-tracking-basic-setup.md) oculare.

### <a name="eye-gaze-pointer-behavior-in-240"></a>Comportamento del puntatore dello sguardo fisso nella versione 2.4.0

Il comportamento del puntatore predefinito dello sguardo fisso è stato modificato in modo che corrisponda al comportamento predefinito del puntatore dello sguardo con la testa. Un puntatore dello sguardo fisso verrà automaticamente eliminato quando viene rilevata una mano. Il puntatore dello sguardo fisso diventerà nuovamente visibile dopo aver detto "Seleziona".

Informazioni dettagliate sulle configurazioni di sguardo fisso e mano sono disponibili [nell'articolo occhi e](../features/input/eye-tracking/eye-tracking-eyes-and-hands.md#how-to-keep-gaze-pointer-always-on) mani.

### <a name="api-changes-in-240"></a>Modifiche all'API nella versione 2.4.0

**Classi controller personalizzate**

Le classi controller personalizzate in precedenza dovevano definire `SetupDefaultInteractions(Handedness)` . Questo metodo è stato reso obsoleto nella versione 2.4, perché il parametro handedness era ridondante con il proprio mani della classe controller. Il nuovo metodo non ha parametri. Inoltre, molte classi controller hanno definito questa operazione nello stesso modo ( ), quindi la chiamata completa è stata sottoposta a refactoring in ed è stato eseguito un override facoltativo `AssignControllerMappings(DefaultInteractions);` `BaseController` anziché obbligatorio.

**Proprietà dello sguardo fisso**

La `UseEyeTracking` proprietà `GazeProvider` dall'implementazione `IMixedRealityEyeGazeProvider` di è stata rinominata in `IsEyeTrackingEnabled` .

Se è stato fatto in precedenza...

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.UseEyeTracking = true;
}
```

Eseguire questa operazione ora...

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.IsEyeTrackingEnabled = true;
}
```

**Proprietà di WindowsApiChecker**

Le proprietà WindowsApiChecker seguenti sono state contrassegnate come obsolete. Usare `IsMethodAvailable` o `IsPropertyAvailable` `IsTypeAvailable` .

- UniversalApiContractV8_IsAvailable
- UniversalApiContractV7_IsAvailable
- UniversalApiContractV6_IsAvailable
- UniversalApiContractV5_IsAvailable
- UniversalApiContractV4_IsAvailable
- UniversalApiContractV3_IsAvailable

Non sono in programma di aggiungere proprietà a WindowsApiChecker per le versioni future del contratto API.

**GltfMeshPrimitiveAttributes di sola lettura**

Gli attributi primitivi della mesh gltf usati per essere impostati sono ora di sola lettura. I relativi valori verranno impostati una sola volta durante la deserializzazione.

### <a name="custom-button-icon-migration"></a>Migrazione dell'icona del pulsante personalizzato

Le icone dei pulsanti personalizzate in precedenza richiedeva l'assegnazione di un nuovo materiale al renderer quad del pulsante. Questa operazione non è più necessaria ed è consigliabile spostare trame di icone personalizzate in un oggetto IconSet. Le icone e i materiali personalizzati esistenti vengono mantenuti. Saranno tuttavia meno ottimali fino all'aggiornamento.
Per aggiornare gli asset in tutti i pulsanti del progetto al nuovo formato consigliato, usare ButtonConfigHelperMigrationHandler.
(Mixed Reality Toolkit -> Utilities -> Migration Window -> Migration Handler Selection -> Microsoft.MixedReality.Toolkit.Utilities.ButtonConfigHelperMigrationHandler)

![Finestra di dialogo Aggiorna](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

Se non viene trovata un'icona nel set di icone predefinito durante la migrazione, verrà creato un set di icone personalizzato in MixedRealityToolkit.Generated/CustomIconSets. Una finestra di dialogo indicherà che l'operazione è stata eseguita.

![Notifica dell'icona personalizzata](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

## <a name="updating-220-to-230"></a>Aggiornamento da 2.2.0 a 2.3.0

- [Modifiche all'API](#api-changes-in-230)

### <a name="api-changes-in-230"></a>Modifiche dell'API nella versione 2.3.0

**ControllerPoseSynchronizer**

Il campo ControllerPoseSynchronizer.handedness privato è stato contrassegnato come obsoleto. Questo dovrebbe avere un impatto minimo sulle applicazioni perché il campo non è visibile all'esterno della relativa classe.

Il setter pubblico della proprietà ControllerPoseSynchronizer.Handedness è stato rimosso ([#7012](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7012)).

**MSBuild per Unity**

Questa versione di MRTK usa una versione più recente di MSBuild per Unity rispetto alle versioni precedenti. Durante il caricamento del progetto, se la versione precedente è elencata nel manifesto di Gestione pacchetti Unity, verrà visualizzata la finestra di dialogo di configurazione con l'opzione Abilita MSBuild per Unity selezionata. L'applicazione eseguirà un aggiornamento.

**ScriptingUtilities**

La classe ScriptingUtilities è stata contrassegnata come obsoleta ed è stata sostituita da ScriptUtilities nell'assembly Microsoft.MixedReality.Toolkit.Editor.Utilities. La nuova classe perfeziona il comportamento precedente e aggiunge il supporto per la rimozione delle definizioni di scripting.

Anche se il codice esistente continuerà a funzionare nella versione 2.3.0, è consigliabile eseguire l'aggiornamento alla nuova classe .

**ShellHandRayPointer**

I membri lineRendererSelected e lineRendererNoTarget della classe ShellHandRayPointer sono stati sostituiti rispettivamente da lineMaterialSelected e lineMaterialNoTarget ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6863)).

Sostituire lineRendererSelected con lineMaterialSelected e/o lineRendererNoTarget con lineMaterialNoTarget per risolvere gli errori di compilazione.

**StartupBehavior dell'osservatore spaziale**

Gli osservatori spaziali compilati sulla classe ora rispettano il valore di `BaseSpatialObserver` StartupBehavior quando vengono ri abilitati ([#6919](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6919)).

Non sono necessarie modifiche per sfruttare i vantaggi di questa correzione.

**Prefab di controllo UX aggiornati per l'uso di PressableButton**

I prefab seguenti usano ora il componente PressableButton invece di TouchHandler per l'interazione da vicino ([7070](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7070))

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

Il codice dell'applicazione potrebbe richiedere l'aggiornamento a causa di questa modifica.

**Spazio dei nomi WindowsMixedRealityUtilities**

Lo spazio dei nomi di WindowsMixedRealityUtilities è stato modificato da Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input a Microsoft.MixedReality.Toolkit.WindowsMixedReality ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6989)).

Aggiornare le #using per risolvere gli errori di compilazione.

## <a name="updating-210-to-220"></a>Aggiornamento da 2.1.0 a 2.2.0

- [Modifiche all'API](#api-changes-in-220)

### <a name="api-changes-in-220"></a>Modifiche dell'API nella versione 2.2.0

**IMixedRealityBoundarySystem.Contains**

Questo metodo in precedenza ha preso in un'enumerazione sperimentale specifica, definita da Unity. Accetta ora un'enumerazione definita da MRTK identica all'enumerazione Unity. Questa modifica consente di preparare MRTK per le API limite future di Unity.

**MixedRealityServiceProfileAttribute**

Per descrivere meglio i requisiti per il supporto di un profilo, MixedRealityServiceProfileAttribute è stato aggiornato per aggiungere una raccolta facoltativa di tipi esclusi. Come parte di questa modifica, la proprietà ServiceType è stata modificata da Type a Type[] ed è stata rinominata RequiredTypes.

È stata aggiunta anche una seconda proprietà, ExcludedTypes.

## <a name="updating-200-to-210"></a>Aggiornamento dalla versione 2.0.0 alla versione 2.1.0

- [Modifiche all'API](#api-changes-in-210)
- [Modifiche del profilo](#profile-changes-in-210)

### <a name="api-changes-in-210"></a>Modifiche all'API nella versione 2.1.0

**BaseNearInteractionTouchable**

È `BaseNearInteractionTouchable` stato modificato per contrassegnare il metodo come `OnValidate` virtuale. Le classi che `BaseNearInteractionTouchable` estendono (ad `NearInteractionTouchableUnityUI` esempio) sono state aggiornate per riflettere questa modifica.

**ColliderNearInteractionTouchable**

La classe `ColliderNearInteractionTouchable` è stata deprecata. Aggiornare i riferimenti al codice per usare `BaseNearInteractionTouchable` .

**IMixedRealityMouseDeviceManager**

**_Aggiunto_**

`IMixedRealityMouseDeviceManager` sono state aggiunte `CursorSpeed` le proprietà `WheelSpeed` e . Queste proprietà consentono alle applicazioni di specificare un valore moltiplicatore in base al quale verrà ridimensionata rispettivamente la velocità del cursore e della rotellina.

Si tratta di una modifica di rilievo e richiede che le implementazioni esistenti di Gestione dispositivi mouse siano modificate.

>[!NOTE]
>Questa modifica non è compatibile con la versione 2.0.0.

**_Deprecato_**

La `MouseInputProfile` proprietà è stata contrassegnata come obsoleta e verrà rimossa da una versione futura di Microsoft Mixed Reality Toolkit. È consigliabile che il codice dell'applicazione non usi più questa proprietà.

**Con interazione**

I metodi e le proprietà seguenti sono stati deprecati e verranno rimossi da una versione futura di Microsoft Mixed Reality Toolkit. È consigliabile aggiornare il codice dell'applicazione in base alle indicazioni contenute nell'attributo Obsolete e visualizzato nella console.

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

La `NearInteractionTouchableSurface` classe è stata aggiunta e ora funge da classe di base per e `NearInteractionTouchable` `NearInteractionTouchableUnityUI` .

### <a name="profile-changes-in-210"></a>Modifiche del profilo nella versione 2.1.0

**Profilo di tracciamento manuale**

La mesh a mano e le visualizzazioni congiunte hanno ora un editor e le impostazioni del giocatore separati. Il profilo di rilevamento manuale è stato aggiornato per consentire l'impostazione di queste visualizzazioni su . Nothing, Everything, Editor o Player.

![Modalità di visualizzazione manuale](../release-notes/images/HandTrackingVisualizationModes.png)

Per il corretto funzionamento con la versione 2.1.0 potrebbe essere necessario aggiornare i profili di tracciamento manuale personalizzati.

>[!NOTE]
>Questa modifica non è compatibile con la versione 2.0.0.

**Profilo di simulazione di input**

Il sistema di simulazione dell'input è stato aggiornato, che modifica alcune impostazioni nel profilo di simulazione di input. Non è possibile eseguire automaticamente la migrazione di alcune modifiche e gli utenti potrebbero scoprire che i profili usano valori predefiniti.

1. Tutte le associazioni keyCode e del pulsante del mouse nel profilo sono state sostituite con uno struct generico, che archivia il tipo di associazione (tasto o mouse) e il codice di associazione effettivo (KeyCode o il numero del pulsante del `KeyBinding` mouse rispettivamente). Lo struct ha un proprio controllo, che consente la visualizzazione unificata e offre uno strumento di "associazione automatica" per impostare rapidamente le associazioni di tasti premendo il rispettivo tasto invece di selezionare da un elenco a discesa enorme.

    - FastControlKey
    - ToggleLeftHandKey
    - ToggleRightHandKey
    - LeftHandManipulationKey
    - RightHandManipulationKey

1. `MouseLookToggle` in precedenza era incluso `MouseLookButton` nell'enumerazione `InputSimulationMouseButton.Focused` come , ora è un'opzione separata. Se abilitata, la fotocamera continuerà a ruotare con il mouse dopo il rilascio del pulsante, fino a quando non viene premuto il tasto di escape.
1. `HandDepthMultiplier` il valore predefinito è stato abbassato da 0,1 a 0,03 per contenere alcune modifiche alla simulazione di input. Se la fotocamera si sposta troppo velocemente durante lo scorrimento, provare ad abbassare questo valore.
1. Le chiavi per ruotare le mani sono state rimosse, la rotazione delle mani è ora controllata anche dal mouse. Tenendo premuto (CTRL) insieme al tasto di manipolazione della mano `HandRotateButton` sinistra/destra (LShift/Space) verrà abilitata la rotazione della mano.
1. È stato introdotto un nuovo asse "UpDown" nell'elenco degli assi di input. Questo controllo controlla lo spostamento della fotocamera in verticale e per impostazione predefinita vengono visualizzati i tasti Q/E, nonché i pulsanti del trigger del controller.

Per altre informazioni su queste modifiche, vedere l'articolo sul servizio [di simulazione dell'input.](../features/input-simulation/input-simulation-service.md)

**Profilo del provider di dati mouse**

Il profilo del provider di dati del mouse è stato aggiornato per esporre le nuove `CursorSpeed` proprietà `WheelSpeed` e . Per i profili personalizzati esistenti verranno forniti automaticamente i valori predefiniti. Quando il profilo viene salvato, questi nuovi valori verranno salvati in modo permanente.

**Profilo di mapping del controller**

Alcuni assi e tipi di input sono stati aggiornati nella versione 2.1.0, in particolare per quanto riguarda la piattaforma OpenVR. Assicurarsi di selezionare **MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles** durante l'aggiornamento. In questo modo, tutti i profili di mapping del controller personalizzati verranno aggiornati con gli assi e i dati aggiornati, lasciando intatte le azioni di input assegnate dall'utente.

## <a name="updating-rc2-to-200"></a>Aggiornamento da RC2 a 2.0.0

Tra le versioni RC2 e 2.0.0 di Microsoft Mixed Reality Toolkit sono state apportate modifiche che potrebbero influire sui progetti esistenti. Questo documento descrive queste modifiche e come aggiornare i progetti alla versione 2.0.0.

- [Modifiche all'API](#api-changes-in-200)
- [Modifiche al nome dell'assembly](#assembly-name-changes-in-200)

### <a name="api-changes-in-200"></a>Modifiche dell'API nella versione 2.0.0

Dopo il rilascio di RC2, sono state apportate alcune modifiche all'API, tra cui alcune che potrebbero interrompere i progetti esistenti. Le sezioni seguenti descrivono le modifiche apportate tra le versioni RC2 e 2.0.0.

**MixedRealityToolkit**

Le proprietà pubbliche seguenti nell'oggetto MixedRealityToolkit sono state deprecate.

- `RegisteredMixedRealityServices` non contiene più la raccolta di servizi di estensioni registrati e provider di dati.

Per accedere ai servizi di estensione, usare `MixedRealityServiceRegistry.TryGetService<T>` . Per accedere ai provider di dati, eseguire il cast dell'istanza del servizio [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) a e usare `GetDataProvider<T>` .

Usare [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) o invece per le proprietà [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) deprecate seguenti

- `ActiveSystems`
- `InputSystem`
- `BoundarySystem`
- `CameraSystem`
- `SpatialAwarenessSystem`
- `TeleportSystem`
- `DiagnosticsSystem`
- `SceneSystem`

**CoreServices**

La classe è la sostituzione delle funzioni di accesso di sistema [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) statiche (ad esempio BoundarySystem) trovate `MixedRealityToolkit` nell'oggetto .

>[!IMPORTANT]
>Le `MixedRealityToolkit` funzioni di accesso di sistema sono state deprecate nella versione 2.0.0 e verranno rimosse in una versione futura di MRTK.

L'esempio di codice seguente illustra il modello precedente e il nuovo modello.

``` c#
// Old
GameObject playAreaVisualization = MixedRealityToolkit.BoundarySystem?.GetPlayAreaVisualization();

// New
GameObject playAreaVisualization = CoreServices.BoundarySystem?.GetPlayAreaVisualization();
```

L'uso della nuova classe CoreSystem garantisce che il codice dell'applicazione non dovrà essere aggiornato se si modifica l'applicazione in modo da usare un registrar del servizio diverso(ad esempio, uno dei gestori di servizi sperimentali).

**IMixedRealityRaycastProvider**

Con l'aggiunta di IMixedRealityRaycastProvider, il profilo di configurazione del sistema di input è stato modificato. Se si dispone di un profilo personalizzato, è possibile che si ricevano gli errori nell'immagine seguente quando si esegue l'applicazione.

![Selezione del provider Raycast 1](../release-notes/images/UnableToRegisterRaycastProvider.png)

Per risolvere questi problemi, aggiungere un'istanza di IMixedRealityRaycastProvider al profilo di sistema di input.

![Selezione del provider Raycast 2](../release-notes/images/SelectRaycastProvider.png)

**Sistema di eventi**

- I `IMixedRealityEventSystem` metodi API obsoleti e sono stati `Register` `Unregister` contrassegnati come obsoleti. Vengono mantenuti per compatibilità con le versioni precedenti.
- `InputSystemGlobalListener` è stato contrassegnato come obsoleto. La funzionalità non è stata modificata.
- `BaseInputHandler` La classe base è stata modificata da `InputSystemGlobalListener` a `InputSystemGlobalHandlerListener` . Si tratta di una modifica di rilievo per tutti i discendenti di `BaseInputHandler` .

**_Motivazione alla base della modifica_**

L'API del sistema di `Register` eventi precedente e potrebbe potenzialmente causare più problemi in fase di `Unregister` esecuzione, ad esempio:

- Se un componente si registra per eventi globali, riceverà eventi di input globali di *tutti i* tipi.
- Se uno dei componenti di un oggetto viene registrato per gli eventi di input globali, tutti i componenti in questo oggetto riceveranno eventi di input globali di *tutti i* tipi.
- Se due componenti nello stesso oggetto vengono registrati in eventi globali e uno viene disabilitato in fase di esecuzione, il secondo smette di ricevere eventi globali.

Nuova API `RegisterHandler` e `UnregisterHandler` :

- Fornisce un controllo esplicito e granulare su quali eventi di input devono essere in ascolto a livello globale e su quali devono essere basati su stato attivo.
- Consente a più componenti nello stesso oggetto di restare in ascolto di eventi globali in modo indipendente l'uno sull'altro.

**_Come eseguire la migrazione_**

- Se l'API è stata `Register` / `Unregister` chiamata direttamente in precedenza, sostituire queste chiamate con chiamate a `RegisterHandler` / `UnregisterHandler` . Usare le interfacce del gestore implementate come parametri generici. Se si implementano più interfacce e molte di esse sono in ascolto di eventi di input globali, chiamare `RegisterHandler` più volte.
- Se si eredita da , modificare `InputSystemGlobalListener` l'ereditarietà in `InputSystemGlobalHandlerListener` . Implementare `RegisterHandlers` e `UnregisterHandlers` astrarre i metodi. Nella chiamata di implementazione ( ) per eseguire la registrazione in tutte le interfacce del gestore per cui si vogliono restare in ascolto `inputSystem.RegisterHandler` `inputSystem.UnregisterHandler` degli eventi globali.
- Se si eredita da `BaseInputHandler` , implementare e `RegisterHandlers` `UnregisterHandlers` astrarre i metodi (come per `InputSystemGlobalListener` ).

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

Le interfacce IMixedRealitySpatialAwarenessSystem e IMixedRealitySpatialAwarenessObserver hanno apportato più modifiche di rilievo, come descritto di seguito.

**_Modifiche_**

I metodi seguenti sono stati rinominati per descriverne meglio l'utilizzo.

- `IMixedRealitySpatialAwarenessSystem.CreateSpatialObjectParent` è stato rinominato in per `IMixedRealitySpatialAwarenessSystem.CreateSpatialAwarenessObservationParent` chiarirne l'utilizzo.

**_Aggiornamenti_**

In base ai commenti e suggerimenti dei clienti, è stato aggiunto il supporto per la rimozione semplice dei dati di consapevolezza spaziale osservati in precedenza.

- `IMixedRealitySpatialAwarenessSystem.ClearObservations()`
- `IMixedRealitySpatialAwarenessSystem.ClearObservations<T>(string name)`
- `IMixedRealitySpatialAwarenessObserver.ClearObservations()`

**Risolutori**

Alcuni componenti del risolutore e la classe di gestione SolverHandler sono stati modificati per correggere vari bug e per un utilizzo più intuitivo.

**_SolverHandler_**

- La classe non si estende più da `ControllerFinder`
- `TrackedObjectToReference` proprietà pubblica deprecata ed è stata rinominata in `TrackedTargetType`
- `TrackedObjectType` deprecazione dei & a destra del controller. Usare invece `MotionController` i valori o e aggiornare la nuova proprietà per limitare il rilevamento al controller sinistro o `HandJoint` `TrackedHandedness` destro

**_Inbetween_**

- `TrackedObjectForSecondTransform` proprietà pubblica deprecata ed è stata rinominata in `SecondTrackedObjectType`
- `AttachSecondTransformToNewTrackedObject()` è stato rimosso. Per aggiornare il risolutore, modificare le proprietà pubbliche, ad esempio `SecondTrackedObjectType`)

**_SurfaceMagnetism_**

- `MaxDistance` la proprietà public è deprecata ed è stata rinominata in `MaxRaycastDistance`
- `CloseDistance` la proprietà public è deprecata ed è stata rinominata in `ClosestDistance`
- Il valore predefinito per è ora il raycast nella direzione della trasformazione `RaycastDirectionMode` della destinazione `TrackedTargetForward` rilevata in avanti
- `OrientationMode`I valori enum `Vertical` e `Full` sono stati rinominati `TrackedTarget` rispettivamente in e `SurfaceNormal`
- `KeepOrientationVertical` È stata aggiunta la proprietà public per controllare se l'orientamento del GameObject associato rimane verticale

**Pulsanti**

- [`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) ora ha `DistanceSpaceMode` la proprietà impostata `Local` su come predefinita. In questo modo i pulsanti possono essere ridimensionati mentre sono ancora a pressione

**Sfera di ritaglio**

L'interfaccia ClippingSphere è stata modificata per rispecchiare le API presenti in ClippingBox e ClippingPlane.

La proprietà Radius di ClippingSphere viene ora calcolata in modo implicito in base alla scala della trasformazione. Prima che gli sviluppatori devono specificare il raggio di ClippingSphere nel controllo. Se si vuole modificare il raggio, è sufficiente aggiornare la scala di trasformazione della trasformazione come di consueto.

**NearInteractionTouchable e PokePointer**

- NearInteractionTouchable non gestisce più il tocco dell'area di disegno dell'interfaccia utente di Unity. La classe NearInteractionTouchableUnityUI deve essere ora usata per i touchable dell'interfaccia utente di Unity.
- ColliderNearInteractionTouchable è la nuova classe di base per i collisori touchable, ad eccezione di NearInteractionTouchableUnityUI.
- BaseNearInteractionTouchable.DistFront è stato spostato e rinominato in PokePointer.TouchableDistance Si tratta della distanza e della quale PokePointer può interagire con i dispositivi toccabili. In precedenza ogni toccabile aveva la propria distanza massima di interazione, ma ora è definita in PokePointer, che consente una migliore ottimizzazione.
- BaseNearInteractionTouchable.DistBack è stato rinominato in PokeThreshold. In questo modo è chiaro che PokeThreshold è la controparte di DebounceThreshold. Un oggetto toccabile viene attivato quando PokeThreshold viene incrociato e rilasciato quando DebounceThreshold viene incrociato.

**ReadOnlyAttribute**

Lo `Microsoft.MixedReality.Toolkit` spazio dei nomi è stato aggiunto a , e `ReadOnlyAttribute` `BeginReadOnlyGroupAttribute` `EndReadOnlyGroupAttribute` .

**PointerClickHandler**

La classe `PointerClickHandler` è stata deprecata. `PointerHandler`L'oggetto deve essere invece usato e fornisce la stessa funzionalità.

**Supporto del clicker HoloLens**

I mapping del controller del clicker HoloLens sono stati modificati da non mano a non [`WindowsMixedRealityController`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityController) mano. [`WindowsMixedRealityGGVHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityGGVHand) A tale scopo, un programma di aggiornamento automatico verrà eseguito la prima volta che si apre il profilo ControllerMapping. Aprire i profili personalizzati almeno una volta dopo l'aggiornamento alla versione 2.0.0 per attivare questo passaggio di migrazione una sola volta.

**InteractableHighlight**

La classe `InteractableHighlight` è stata deprecata. In `InteractableOnFocus` alternativa, `FocusInteractableStates` è necessario usare la classe e l'asset. Per creare un nuovo asset per , fare clic con il pulsante destro del mouse nella finestra `Theme` del progetto e scegliere Crea `InteractableOnFocus` *tema*  >  interagiscibile di Mixed Reality  >    >  Toolkit.

**HandInteractionPanZoom**

`HandInteractionPanZoom` è stato spostato nello spazio dei nomi dell'interfaccia utente perché non era un componente di input. `HandPanEventData` è stato anche spostato in questo spazio dei nomi e semplificato in modo da corrispondere ad altri dati dell'evento dell'interfaccia utente.

### <a name="assembly-name-changes-in-200"></a>Modifiche al nome dell'assembly nella versione 2.0.0

Nella versione 2.0.0 tutti i nomi di assembly ufficiali di Mixed Reality Toolkit e i relativi file di definizione dell'assembly (asmdef) associati sono stati aggiornati in base al modello seguente.

```c#
Microsoft.MixedReality.Toolkit[.<name>]
```

In alcuni casi, sono stati uniti più assembly per creare una migliore unità del contenuto. Se il progetto usa file asmdef personalizzati, potrebbe essere necessario aggiornarsi.

Le tabelle seguenti descrivono il mapping dei nomi di file con estensione asmdef RC2 alla versione 2.0.0. Tutti i nomi degli assembly corrispondono al nome del file asmdef.

**MixedRealityToolkit**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit.asmdef | Microsoft.MixedReality.Toolkit.asmdef |
| MixedRealityToolkit.Core.BuildAndDeploy.asmdef | Microsoft.MixedReality.Toolkit.Editor.BuildAndDeploy.asmdef |
| MixedRealityToolkit.Core.Definitions.Utilities.Editor.asmdef | Rimosso, usare Microsoft.MixedReality.Toolkit.Editor.Utilities.asmdef |
| MixedRealityToolkit.Core.Extensions.EditorClassExtensions.asmdef | Microsoft.MixedReality.Toolkit.Editor.ClassExtensions.asmdef
| MixedRealityToolkit.Core.Inspectors.asmdef | Microsoft.MixedReality.Toolkit.Editor.Inspectors.asmdef |
| MixedRealityToolkit.Core.Inspectors.ServiceInspectors.asmdef | Microsoft.MixedReality.Toolkit.Editor.ServiceInspectors.asmdef |
| MixedRealityToolkit.Core.UtilitiesAsync.asmdef | Microsoft.MixedReality.Toolkit.Async.asmdef |
| MixedRealityToolkit.Core.Utilities.Editor.asmdef | Microsoft.MixedReality.Toolkit.Editor.Utilities.asmdef |
| MixedRealityToolkit.Utilities.Gltf.asmdef | Microsoft.MixedReality.Toolkit.Gltf.asmdef |
| MixedRealityToolkit.Utilities.Gltf.Importers.asmdef | Microsoft.MixedReality.Toolkit.Gltf.Importers.asmdef |

**MixedRealityToolkit.Providers**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit.Providers.OpenVR.asmdef | Microsoft.MixedReality.Toolkit.Providers.OpenVR.asmdef |
| MixedRealityToolkit.Providers.WindowsMixedReality.asmdef | Microsoft.MixedReality.Toolkit.Providers.WindowsMixedReality.asmdef |
| MixedRealityToolkit.Providers.WindowsVoiceInput.asmdef | Microsoft.MixedReality.Toolkit.Providers.WindowsVoiceInput.asmdef |

**MixedRealityToolkit.Services**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit.Services.BoundarySystem.asmdef | Microsoft.MixedReality.Toolkit.Services.BoundarySystem.asmdef |
| MixedRealityToolkit.Services.CameraSystem.asmdef | Microsoft.MixedReality.Toolkit.Services.CameraSystem.asmdef |
| MixedRealityToolkit.Services.DiagnosticsSystem.asmdef | Microsoft.MixedReality.Toolkit.Services.DiagnosticsSystem.asmdef |
| MixedRealityToolkit.Services.InputSimulation.asmdef | Microsoft.MixedReality.Toolkit.Services.InputSimulation.asmdef |
| MixedRealityToolkit.Services.InputSimulation.Editor.asmdef | Microsoft.MixedReality.Toolkit.Services.InputSimulation.Editor.asmdef |
| MixedRealityToolkit.Services.InputSystem.asmdef | Microsoft.MixedReality.Toolkit.Services.InputSystem.asmdef |
| MixedRealityToolkit.Services.Inspectors.asmdef | Microsoft.MixedReality.Toolkit.Services.InputSystem.Editor.asmdef |
| MixedRealityToolkit.Services.SceneSystem.asmdef | Microsoft.MixedReality.Toolkit.Services.SceneSystem.asmdef |
| MixedRealityToolkit.Services.SpatialAwarenessSystem.asmdef | Microsoft.MixedReality.Toolkit.Services.SpatialAwarenessSystem.asmdef |
| MixedRealityToolkit.Services.TeleportSystem.asmdef | Microsoft.MixedReality.Toolkit.Services.TeleportSystem.asmdef |

**MixedRealityToolkit.SDK**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit.SDK.asmdef | Microsoft.MixedReality.Toolkit.SDK.asmdef |
| MixedRealityToolkit.SDK.Inspectors.asmdef | Microsoft.MixedReality.Toolkit.SDK.Inspectors.asmdef |

**MixedRealityToolkit.Examples**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit.Examples.asmdef | Microsoft.MixedReality.Toolkit.Examples.asmdef |
| MixedRealityToolkit.Examples.Demos.Gltf.asmdef | Microsoft.MixedReality.Toolkit.Demos.Gltf.asmdef |
| MixedRealityToolkit.Examples.Demos.StandardShader.Inspectors.asmdef | Microsoft.MixedReality.Toolkit.Demos.StandardShader.Inspectors.asmdef |
| MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.asmdef | Microsoft.MixedReality.Toolkit.Demos.InspectorFields.asmdef |
| MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.Inspectors.asmdef | Microsoft.MixedReality.Toolkit.Demos.InspectorFields.Inspectors.asmdef |
| MixedRealityToolkit.Examples.Demos.UX.Interactables.asmdef | Microsoft.MixedReality.Toolkit.Demos.UX.Interactables.asmdef |