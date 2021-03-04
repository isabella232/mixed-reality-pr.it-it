---
title: ReleaseNotes
description: Release abbiend della versione corrente di MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 850605855ff756939c334bf8116022a1340aa9f6
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783133"
---
# <a name="microsoft-mixed-reality-toolkit-release-notes"></a>Note sulla versione di Microsoft Mixed Reality Toolkit

- [Novità](#whats-new-in-240)
- [Modifiche di rilievo](#breaking-changes-in-240)
- [Aggiornamento delle linee guida](upgrading.md#upgrading-to-a-new-version-of-mrtk)
- [Problemi noti](#known-issues-in-240)

Questa versione di Microsoft Mixed Reality Toolkit supporta i dispositivi e le piattaforme seguenti.

- Microsoft HoloLens 2
- Microsoft HoloLens (1a generazione)
- Cuffie immersive della realtà mista di Windows
- OpenVR
- Sperimentale Piattaforma Unity 2019,3 XR
- Mobile AR tramite Unity AR Foundation
  - Android
  - iOS
- Tracciamento della mano Ultraleap

Il software seguente è obbligatorio.

- [Microsoft Visual Studio](https://visualstudio.microsoft.com) (2017 o 2019) Community Edition o versione successiva
- [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 18362 o versione successiva (installato dal programma di installazione di Visual Studio)
- [Unity](https://unity3d.com/get-unity/download) 2018,4 LTS o 2019 (2019,3 consigliato)

**Scaricare**

[Microsoft. MixedReality. Toolkit. Unity. Foundation. 2.4.0. file unitypackage Tools](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage) 
 [Microsoft. MixedReality. Toolkit. Unity. Extensions. 2.4.0. file unitypackage Tools](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Extensions.2.4.0.unitypackage) 
 [Microsoft. MixedReality. Toolkit. Unity. examples. 2.4.0. file unitypackage Tools](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Examples.2.4.0.unitypackage) 
 [Microsoft. MixedReality. Toolkit. Unity. Tools. 2.4.0. file unitypackage Tools](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Tools.2.4.0.unitypackage)

Altri file sono disponibili nella pagina della [versione di GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.4.0)

**Requisiti di NuGet**

Se si importano i [pacchetti NuGet del Toolkit per realtà mista](../reference-docs/MRTKNuGetPackage.md), è consigliabile utilizzare il seguente software.

- [NuGet per Unity 2.0.0 o versione successiva](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)

### <a name="whats-new-in-240"></a>Novità di 2.4.0

**Supporto di Ultraleap Hand Tracking**

La [provider di dati di movimento intercalare](../features/CrossPlatform/LeapMotionMRTK.md) consente di tenere traccia della mano articolata per le applicazioni VR ed è utile anche per la prototipazione rapida dell'editor.  Il provider di dati può essere configurato in modo da usare il controller di movimento Leap montato su un auricolare o posizionato su una scrivania.

Per utilizzare questo provider di dati, è necessario un [controller di movimento Leap](https://www.ultraleap.com/product/leap-motion-controller/) .

![LeapMotionIntroGif](../features/Images/CrossPlatform/LeapMotion/LeapMotionSideBySide2.gif)

**Finestra di migrazione**

![Finestra di migrazione](../features/Images/MigrationWindow/MRTK_Migration_Window.png)

MRTK ora è dotato di uno strumento di migrazione che consente di aggiornare i componenti deprecati alle versioni più recenti e di garantire il funzionamento del codice esistente anche quando MRTK apporta modifiche di rilievo.

**È in genere consigliabile eseguire lo strumento di migrazione dopo aver effettuato il pull di una nuova versione di MRTK** per garantire che la maggior parte del progetto verrà automaticamente adattata al codice MRTK più recente.

La [finestra di migrazione](../features/Tools/MigrationWindow.md) si trova in "Mixed Reality Toolkit > Utilities > finestra di migrazione". Fa parte del pacchetto di **strumenti** .

Attualmente supporta:

- Aggiornamento di ManipulationHandler e BoundingBox alle versioni più recenti ObjectManipulator e BoundsControl.
- Aggiornamento delle icone dei pulsanti personalizzati per funzionare correttamente con il nuovo Helper config del pulsante.

Si noti che BoundsControl è ancora in fase sperimentale e pertanto le API o le proprietà potrebbero ancora cambiare nella versione successiva.

**Modifiche al layout della cartella MRTK**

Questa versione di MRTK modifica il layout della struttura di cartelle MRTK. Questa modifica incapsula tutto il codice MRTK in una singola gerarchia di cartelle e riduce la lunghezza totale del percorso di tutti i file MRTK.

| Cartella precedente | Nuova cartella |
| --- | --- |
| MixedRealityToolkit | MRTK\Core |
| MixedRealityToolkit. examples | MRTK\Examples |
| MixedRealityToolkit. Extensions | MRTK\Extensions |
| MixedRealityToolkit. Providers | MRTK\Providers |
| MixedRealityToolkit. SDK | MRTK\SDK |
| MixedRealityToolkit. Services | MRTK\Services |
| MixedRealityToolkit. test | MRTK\Tests |
| MixedRealityToolkit. Tools | MRTK\Tools |

> [!IMPORTANT]
> `MixedRealityToolkit.Generated`Contiene i file generati dal cliente e rimane invariato.

**Casella degli strumenti MRTK**

![Casella degli strumenti MRTK](../features/Images/Tools/MRTKToolboxWindow.png)

La [casella degli strumenti MRTK](../features/README_Toolbox.md) è un'utilità della finestra dell'editor di Unity che semplifica l'individuazione e la generazione di componenti prefabbricati di MRTK UX nella scena corrente. Gli elementi possono essere filtrati nella visualizzazione tramite la barra di ricerca nella parte superiore della finestra. La finestra casella degli strumenti è progettata per generare MRTK prefabbricati predefiniti nella scena corrente.

**Toccare per posizionare**

[Toccare per posizionare](../features/README_TapToPlace.md) è un componente di interazione molto usato per posizionare facilmente un oggetto gioco sulla superficie. Toccare per posizionare usa una combinazione di due clic e movimento Head per inserire un oggetto.

![TapToPlace](../features/Images/Solver/TapToPlace/TapToPlaceIntroGif.gif)

**Helper config Button aggiunto ai pulsanti** 
 ![ stampabili Button config helper ](https://user-images.githubusercontent.com/9789716/70167111-e3175600-167a-11ea-9c52-444509c06105.gif) questa nuova funzionalità semplifica la modifica dell'icona e del testo dei pulsanti. L'icona supporta la trama del tipo di carattere SDF di quad, sprite e TextMesh Pro. Per informazioni dettagliate, vedere la [documentazione del pulsante](../features/README_Button.md#how-to-change-the-icon-and-text) di MRTK.

**Nuovi pulsanti di alternanza di stile HoloLens 2-CheckBox, Switch, Radio**
<br/><img src="https://user-images.githubusercontent.com/13754172/75299797-df631d80-57ea-11ea-8857-8ef647df0aca.gif" width="450" alt="Button Config Helper">
<br/><img src="https://user-images.githubusercontent.com/13754172/75299783-d6724c00-57ea-11ea-88b1-85e4a585212f.gif" width="450" alt="Pressabe button">

**Miglioramenti del menu a mano**

Il menu a mano è stato adattato in molte applicazioni. Uno dei principali problemi riscontrati è la falsa attivazione accidentale durante la manipolazione degli oggetti o l'interazione con altri contenuti e così via. È stata aggiunta una nuova opzione di attivazione dello sguardo a HandConstraintPalmUp.cs per impedire l'attivazione di false. Con questa opzione, il menu non viene visualizzato accidentalmente, fino a quando l'utente non guarda la mano.<br/>
![0416_HandMenu_02](https://user-images.githubusercontent.com/13754172/79507261-4aabbd80-7fec-11ea-95c4-6e3f4bd18c11.gif)

**Aggiornamento degli esempi di menu a mano**

Nuovo Esempio di interazione di menu di grandi dimensioni 1: selezionare & menu di pull per il blocco globale<br/>
![0416_HandMenu_03](https://user-images.githubusercontent.com/13754172/79507983-90b55100-7fed-11ea-9062-630c892950cb.gif)

Nuovo Esempio di interazione di menu di grandi dimensioni 2-blocco globale automatico a mano<br/>
![0416_HandMenu_04](https://user-images.githubusercontent.com/13754172/79508227-f9043280-7fed-11ea-995f-ac3cfe42fe65.gif)

**Finestra di dialogo (sperimentale)**
<br/><img src="../features/Images/Dialog/MRTK_UX_Dialog_Main.png" width="450" alt="UX Dialog Box">

L'interfaccia utente della finestra di dialogo è stata trasferita da HoloToolkit con nuovi aggiornamenti di progettazione di tipo Shell HoloLens 2.

**Ancoraggio (sperimentale)**
<br/><img src="https://user-images.githubusercontent.com/621574/76669327-65e86080-6548-11ea-85a3-f84f6b367f97.gif" width="450" alt="Dock">

Questo controllo consente lo spostamento di oggetti all'interno e all'esterno di posizioni predeterminate, per la creazione di tavolozze, scaffali e barre di spostamento.

**Marcatori del profiler Unity**

Questa versione di MRTK ha aggiunto marcatori del profiler Unity al sistema di input e ai provider di dati. Questi marcatori forniscono informazioni dettagliate sul punto in cui viene impiegato il tempo nel sistema di input MRTK che può essere usato per ottimizzare le applicazioni.

I marcatori accettano il formato "[MRTK] ClassWithoutNamespace. Method".

![Marcatori Profiler](../features/Images/ReleaseNotes/ProfilerMarkers.png)

**WindowsApiChecker: IsMethodAvailable (), IsPropertyAvailable () e IsTypeAvailable ()**

Questa versione di MRTK aggiunge tre nuovi metodi alla [`WindowsApiChecker`](xref:Microsoft.MixedReality.Toolkit.Windows.Utilities.WindowsApiChecker) classe: `IsMethodAvailable` `IsPropertyAvailable` e `IsTypeAvailable` . Questi metodi consentono di verificare il supporto delle funzionalità in Windows 10 e sono preferiti rispetto all'uso delle `UniversalApiContractV#_IsAvailable` Proprietà.

**Helper per ottenere campi di input di testo che utilizzano MixedRealityKeyboard per UnityUI, TextMeshPro (sperimentale)**

<img src="https://user-images.githubusercontent.com/168492/77582981-86e07800-6e9d-11ea-86e5-bf2c0840296c.png" width="300" alt="MRTK Keyboard for unity" />

Sono stati introdotti due componenti helper [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) che possono essere aggiunti a campi di input di testo nell'interfaccia utente di Unity per consentire la visualizzazione della tastiera HoloLens 2 e Windows Mixed Reality quando si fa clic sui campi.

Per ulteriori informazioni, vedere gli [helper della tastiera per la realtà mista](../reference-docs/MixedRealityKeyboard/README_MixedRealityKeyboard.md).

**Opzioni di allineamento della raccolta di oggetti Grid**

<img src="https://user-images.githubusercontent.com/39840334/79289136-5c228780-7e7d-11ea-82b4-07959e42c3ed.gif" width="300" alt="Alignment Options" />

È stata aggiunta la possibilità di scegliere il modo in cui gli elementi della griglia sono allineati, se sono allineati al centro o lungo l'asse sinistro/destro (asse superiore/inferiore quando si esegue la riga e il layout della colonna)

**Modifiche all'ancoraggio della raccolta di oggetti Grid**

<img src="https://user-images.githubusercontent.com/39840334/79516745-17bff480-8001-11ea-8492-cfa953c451da.gif" width="300" alt="Anchor Changes" />

Sono state apportate modifiche al comportamento della raccolta di oggetti Grid in linea con i comportamenti dei gruppi di layout di Unity allineando l'ancoraggio lungo l'asse centrale di un oggetto. Il comportamento precedente della raccolta di oggetti Grid può essere attivato o disattivato con il `AnchorAlongAxis` campo.

**Controllo della fotocamera della simulazione di input adattato**

La velocità di controllo della fotocamera con la simulazione di input nell'editor è più lenta per un'esperienza più uniforme e ora è disconnessa da framerate. Controllo rapido della fotocamera attivato ora con spostamento a destra anziché CTRL

**Simulazione di input GGV senza intervento**

<img src="https://user-images.githubusercontent.com/39840334/79164615-40908180-7d96-11ea-8195-6be34d4df8d6.gif" width="300" alt="Hands-free GGV input"/>

È stata abilitata la possibilità di interagire con gli oggetti senza portare a termine il servizio di simulazione input dell'editor. Ruotare la fotocamera in modo che il cursore dello sguardo si trovi su un oggetto interagibile e fare clic sul pulsante sinistro del mouse per interagire con esso.

**Helper config pulsante**

<img src="https://user-images.githubusercontent.com/168492/81211778-bb5d4e80-8f88-11ea-94c7-33cf265586df.png" width="300" alt="Button Config Helper" />

Button config Helper è una funzionalità dell'editor che semplifica la personalizzazione dei pulsanti MRTK. Ora è molto più semplice:

- Aggiornare il testo dell'etichetta del pulsante
- Aggiungere un listener di eventi click del pulsante
- Modificare l'icona del pulsante

**Selezione Spatializer audio nella finestra di dialogo di configurazione di MRTK**

È ora possibile specificare il Spatializer audio nella finestra di dialogo di configurazione di MRTK. L'installazione di nuovi spatializers, ad esempio [Microsoft Spatializer](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/), verrà riattivata per consentire una selezione semplificata.

![Configurazione di MRTK selezionare Spatializer](../features/Images/ReleaseNotes/SpatializerSelection.png)

**Manipolatore di oggetti laureato in SDK**

![Manipolatore di oggetti](../features//Images/ManipulationHandler/MRTK_Manipulation_Main.png)

ObjectManipulator è ora laureato in SDK e non è più una funzionalità sperimentale. Questo controllo sostituisce la classe ManipulationHandler esistente, che ora è deprecata. ObjectManipulator è dotato di un nuovo sistema di vincoli più flessibile e risponde correttamente alla fisica. Un elenco completo di funzionalità e istruzioni per la configurazione sono disponibili nella [documentazione relativa al manipolatore di oggetti](../features/README_ObjectManipulator.md).
Gli utenti possono sfruttare la nuova [finestra di migrazione](../features/Tools/MigrationWindow.md) per aggiornare la GameObject esistente usando ManipulationHandler a ObjectManipulator

**Miglioramenti del controllo dei limiti**

Il code coverage del test è stato notevolmente aumentato per il controllo dei limiti di questa versione ed è stato risolto uno dei principali punti deboli degli utenti del riquadro: il controllo dei limiti ora non ricreerà più gli oggetti visivi nelle modifiche di configurazione. Ora supporta anche la riconfigurazione di qualsiasi proprietà durante il Runtime. Inoltre, le proprietà DrawTetherWhenManipulating e HandlesIgnoreCollider sono ora configurabili per tipo di handle.

### <a name="breaking-changes-in-240"></a>Modifiche di rilievo in 2.4.0

**API sguardi occhi**

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

**Configurazione degli sguardi**

Questa versione di MRTK modifica i passaggi necessari per l'installazione di Eye sguardi. È possibile trovare la casella di controllo _' IsEyeTrackingEnabled '_ nelle impostazioni di sguardi del profilo puntatore di input. Se si seleziona questa casella, verrà abilitato lo sguardo basato sull'occhio, anziché lo sguardo predefinito basato sulla testa.

Per ulteriori informazioni su queste modifiche e istruzioni complete per la configurazione della verifica degli occhi, vedere l'articolo relativo alla [Verifica](../features/EyeTracking/EyeTracking_BasicSetup.md) degli occhi.

### <a name="known-issues-in-240"></a>Problemi noti in 2.4.0

**La finestra di dialogo MRTK Configurator non Mostra ' Abilita MSBuild per Unity ' in Unity 2019,3**

Esiste un problema per cui l'abilitazione di MSBuild per Unity in 2019,3 può comportare un ciclo infinito di ripristino dei pacchetti ([#7239](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7239)).

Come soluzione alternativa, è possibile importare il pacchetto Microsoft. Windows. DotNetWinRT usando [NuGet per Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest).

**Versione dell'assembly duplicata e più assembly precompilati Unity 2018,4**

Se la piattaforma è cambiata da autonomo a UWP e quindi di nuovo a autonomo in Unity 2018,4, potrebbero essere presenti gli errori seguenti nella console:

```
PrecompiledAssemblyException: Multiple precompiled assemblies with the same name Microsoft.Windows.MixedReality.DotNetWinRT.dll included for the current platform. Only one assembly with the same name is allowed per platform. Assembly paths
```

```
Assets\MRTK\Examples\Demos\HandTracking\Scenes\Utilities\InspectorFields\AssemblyInfo.cs(6,12): error CS0579: Duplicate 'AssemblyVersion' attribute
```

Questi errori sono causati da problemi nel processo di eliminazione con MSBuildForUnity.  Per risolvere il problema, mentre si è in modalità autonoma, eliminare la cartella dipendenze nella radice degli asset e riavviare Unity.

Per altri dettagli, vedere il [problema 7948](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7948).

**Applicazioni visualizzate come lavagna 2D in Unity 2019,3**

Quando si usa Unity 2019,3, l'abilitazione del supporto di XR non configura un SDK (legacy) o un plug-in predefinito (XR Management). Di conseguenza, le applicazioni sono vincolate a uno Slate 2D. Per informazioni dettagliate sulla risoluzione, vedere l' [articolo compilazione e distribuzione di MRTK](../updates-deployment/BuildAndDeploy.md#unity-20193-and-hololens).

**Unity 2019,3: architettura di compilazione ARM**

Si è verificato un [problema noto](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2) in unity 2019,3 che causa errori quando si seleziona ARM come architettura di compilazione in Visual Studio. La soluzione consigliata consiste nel compilare per ARM64. Se questa opzione non è possibile, disabilitare i **processi grafici** in **modifica**  >  **Impostazioni progetto**  >  **lettore**  >  **altre impostazioni**. Per ulteriori informazioni [, vedere compilazione e distribuzione](../updates-deployment/BuildAndDeploy.md#unity-20193-and-hololens).

**Swapping del profilo di runtime**

MRTK non supporta completamente lo swapping del profilo in fase di esecuzione. Questa funzionalità viene esaminata per una versione futura. Per ulteriori informazioni, vedere i problemi [4289](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/4289), [5465](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5465) e [5466](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5466) .

**Unity 2018: back-end .NET ed AR Foundation**

Si è verificato un problema in Unity 2018, in cui la compilazione di un progetto piattaforma UWP (Universal Windows Platform) usando il back-end di scripting .NET, il pacchetto di Unity AR Foundation avrà esito negativo.

Per risolvere il problema, eseguire una delle operazioni seguenti:

- Passare il back-end di scripting a IL2CPP
- Nella finestra impostazioni di compilazione deselezionare * * Unity progetti C# "
