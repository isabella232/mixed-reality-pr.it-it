---
title: MixedRealityConfigurationGuide
description: Documentazione per la configurazione di MRTK in Unity.
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 7b5dfd71869ba0470e9c14b1d0db4fc9d94840ef
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782010"
---
# <a name="mixed-reality-toolkit-profile-configuration-guide"></a>Guida alla configurazione del profilo del Toolkit di realtà mista

![Logo di MRTK](../features/images/MRTK_Logo_Rev.png)

Il Toolkit di realtà mista centralizza la maggior parte della configurazione necessaria per gestire il Toolkit come possibile (ad eccezione di true Runtime "Things").

Questa guida è una semplice procedura dettagliata per ogni schermata del profilo di configurazione attualmente disponibile per il Toolkit.

## <a name="the-main-mixed-reality-toolkit-configuration-profile"></a>Il profilo di configurazione principale di Mixed Reality Toolkit

Il profilo di configurazione principale, associato al GameObject *MixedRealityToolkit* nella scena, fornisce il punto di ingresso principale per il Toolkit nel progetto.

> [!NOTE]
> Il Toolkit di realtà mista "blocca" le schermate di configurazione predefinite per assicurarsi di avere sempre un punto iniziale comune per il progetto ed è consigliabile iniziare a definire le proprie impostazioni durante l'evoluzione del progetto. La configurazione di MRTK non è modificabile durante la modalità di riproduzione.

![Profilo di configurazione di MRTK](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ActiveConfiguration.png)

Tutti i profili "predefiniti" per il Toolkit di realtà mista sono disponibili nel progetto SDK nella cartella assets/MRTK/SDK/Profiles.

> [!IMPORTANT]
> DefaultHoloLens2ConfigurationProfile è ottimizzato per HoloLens 2. Per informazioni dettagliate, vedere [profili](../features/profiles/Profiles.md) .

Quando si apre il profilo di configurazione principale del Toolkit di realtà mista, viene visualizzata la schermata seguente nel controllo:

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_MixedRealityToolkitConfigurationScreen.png" width="650px" alt="Configuration Screen" style="display:block;">

Se si seleziona un asset MixedRealityToolkitConfigurationProfile senza MixedRealityToolkit nella scena, verrà chiesto se si desidera che il MRTK Configure automaticamente la scena. Questa operazione è facoltativa, tuttavia, per accedere a tutte le schermate di configurazione deve essere presente un oggetto MixedRealityToolkit attivo nella scena.

In questo modo viene ospitata la configurazione di runtime attiva corrente per il progetto.

Da qui è possibile passare a tutti i profili di configurazione per MRTK, tra cui:

- [Guida alla configurazione del profilo del Toolkit di realtà mista](#mixed-reality-toolkit-profile-configuration-guide)
  - [Il profilo di configurazione principale di Mixed Reality Toolkit](#the-main-mixed-reality-toolkit-configuration-profile)
  - [Impostazioni esperienza](#experience-settings)
  - [Impostazioni della fotocamera](#camera-settings)
  - [Impostazioni del sistema di input](#input-system-settings)
  - [Impostazioni visualizzazione limite](#boundary-visualization-settings)
  - [Selezione del sistema di Teleportation](#teleportation-system-selection)
  - [Impostazioni di consapevolezza spaziale](#spatial-awareness-settings)
  - [Impostazioni di diagnostica](#diagnostics-settings)
  - [Impostazioni del sistema di scena](#scene-system-settings)
  - [Impostazioni servizi aggiuntivi](#additional-services-settings)
  - [Impostazioni azioni di input](#input-actions-settings)
  - [Regole azioni di input](#input-actions-rules)
  - [Configurazione puntatore](#pointer-configuration)
  - [Configurazione di movimenti](#gestures-configuration)
  - [Comandi vocali](#speech-commands)
  - [Configurazione mapping controller](#controller-mapping-configuration)
  - [Impostazioni di visualizzazione del controller](#controller-visualization-settings)
  - [Utilità Editor](#editor-utilities)
    - [Controlli servizio](#service-inspectors)
    - [Renderer buffer profondità](#depth-buffer-renderer)
  - [Modifica dei profili in fase di esecuzione](#changing-profiles-at-runtime)
  - [Scambio di profili prima dell'inizializzazione di MRTK](#swapping-profiles-prior-to-mrtk-initialization)
  - [Vedere anche](#see-also)

Questi profili di configurazione sono descritti in dettaglio nelle sezioni pertinenti:

---
<a name="experience"></a>

## <a name="experience-settings"></a>Impostazioni esperienza

Situato nella pagina di configurazione principale del Toolkit di realtà mista, questa impostazione definisce l'operazione predefinita della [scala dell'ambiente di realtà mista](https://docs.microsoft.com/windows/mixed-reality/coordinate-systems-in-unity) per il progetto.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ExperienceSettings.png" width="650px" alt="Experience Settings" style="display:block;">

---
<a name="camera"></a>

## <a name="camera-settings"></a>Impostazioni della fotocamera

Le impostazioni della fotocamera definiscono come verrà configurata la fotocamera per il progetto di realtà mista, definendo le impostazioni generiche di ritaglio, qualità e trasparenza.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_CameraProfile.png" width="650px" alt="Camara Settings" style="display:block;">

---
<a name="inputsystem"></a>

## <a name="input-system-settings"></a>Impostazioni del sistema di input

Il progetto di realtà mista fornisce un sistema di input solido e ben preparato per il routing di tutti gli eventi di input intorno al progetto selezionato per impostazione predefinita.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemSelection.png" width="650px" alt="Input System setting selection" style="display:block;">

Dietro il sistema di input fornito da MRTK sono disponibili diversi altri sistemi, che consentono di gestire e gestire le complesse interoperabilità necessarie per astrarre le complessità di un Framework multipiattaforma/realtà mista.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemProfile.png" width="650px" alt="Input system profile setting" style="display:block;">

Di seguito sono elencati i singoli profili:

- Impostazioni stato attivo
- [Impostazioni azioni di input](#input-actions-settings)
- [Regole azioni di input](#input-actions-rules)
- [Configurazione puntatore](#pointer-configuration)
- [Configurazione di movimenti](#gestures-configuration)
- [Comandi vocali](#speech-commands)
- [Configurazione mapping controller](#controller-mapping-configuration)
- [Impostazioni di visualizzazione del controller](#controller-visualization-settings)

---
<a name="boundary"></a>

## <a name="boundary-visualization-settings"></a>Impostazioni visualizzazione limite

Il sistema di limiti converte il limite percepito segnalato dal sistema di confine/sorveglianza delle piattaforme sottostanti. La configurazione del Visualizzatore di limiti consente di visualizzare automaticamente il limite registrato nella scena rispetto alla posizione dell'utente. Il limite viene anche reattivo/aggiornato in base alla posizione in cui l'utente si trasferisce nella scena.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_BoundaryVisualizationProfile.png" width="650px" alt="Boundry Visualization" style="display:block;">

---
<a name="teleportation"></a>

## <a name="teleportation-system-selection"></a>Selezione del sistema di Teleportation

Il progetto di realtà mista fornisce un sistema di teleporte completo per la gestione di eventi di teleportazione nel progetto selezionato per impostazione predefinita.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_TeleportationSystemSelection.png" width="650px" alt="Teleportion system selection" style="display:block;">

---
<a name="spatialawareness"></a>

## <a name="spatial-awareness-settings"></a>Impostazioni di consapevolezza spaziale

Il progetto di realtà mista fornisce un sistema di riconoscimento spaziale ricompilato per l'utilizzo di sistemi di analisi spaziale nel progetto selezionato per impostazione predefinita.
Qui è possibile visualizzare l'architettura dietro il [sistema di riconoscimento spaziale MRTK](../architecture/SpatialAwareness.md).

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessSystemSelection.png" width="650px" alt="Spatial Awarensess System selelction" style="display:block;">

La configurazione della consapevolezza spaziale del Toolkit di realtà mista consente di personalizzare la modalità di avvio del sistema, se è automaticamente quando l'applicazione viene avviata o successivamente a livello di codice, nonché come impostare gli extent per il campo di visualizzazione.

Consente inoltre di configurare le impostazioni della rete e della superficie, personalizzando ulteriormente il modo in cui il progetto riconosce l'ambiente.

Questa operazione è applicabile solo ai dispositivi che possono fornire un ambiente analizzato.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessProfile.png" width="650px" alt="Spatial Awareness profile" style="display:block;">

---
<a name="diagnostic"></a>

## <a name="diagnostics-settings"></a>Impostazioni di diagnostica

Una funzionalità facoltativa ma estremamente utile di MRTK è la funzionalità di diagnostica del plug-in.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsSystemSelection.png" width="650px" alt="Diagnostics system selection" style="display:block;">

Il profilo di diagnostica fornisce diversi sistemi semplici da monitorare durante l'esecuzione del progetto, inclusa un'opzione di attivazione/disattivazione utile per abilitare o disabilitare il pannello di visualizzazione nella scena.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsProfile.png" width="650px" alt="Diagonostic profile" style="display:block;">

---
<a name="scenesystem"></a>

## <a name="scene-system-settings"></a>Impostazioni del sistema di scena

MRTK fornisce questo servizio facoltativo che consente di gestire il caricamento e lo scaricamento di scene additive complesse. Per decidere se il sistema di scena costituisce una scelta ottimale per il progetto, vedere la pagina relativa al [sistema della scena Introduzione Guida.](../features/scene-system/SceneSystemGettingStarted.md)

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SceneSystemProfile.png" width="650px" alt="Scene System settings" style="display:block;">

---
<a name="services"></a>

## <a name="additional-services-settings"></a>Impostazioni servizi aggiuntivi

Una delle aree più avanzate del Toolkit di realtà mista è l'implementazione del [modello del localizzatore di servizi](https://en.wikipedia.org/wiki/Service_locator_pattern) che consente la registrazione di qualsiasi "servizio" con il Framework. In questo modo è possibile estendere il Framework con nuove funzionalità o sistemi, ma anche consentire ai progetti di sfruttare queste funzionalità per registrare i propri componenti Runtime.

Qualsiasi servizio registrato ottiene comunque il vantaggio completo di tutti gli eventi di Unity, senza l'overhead e i costi di implementazione di un monocomportamento o di modelli singleton goffi. Questo consente i componenti C# puri senza overhead di scena per l'esecuzione di processi in primo piano e in background, ad esempio i sistemi di generazione, la logica del gioco di runtime o praticamente qualsiasi altra cosa.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_RegisteredServiceProvidersProfile.png" width="650px" alt="Additional servicess settings" style="display:block;">

---
<a name="inputactions"></a>

## <a name="input-actions-settings"></a>Impostazioni azioni di input

Le azioni di input consentono di astrarre eventuali interazioni fisiche e input da un progetto di Runtime. Tutto l'input fisico (da controller/mano/mouse/ecc) viene convertito in un'azione di input logica da usare nel progetto di Runtime. In questo modo, indipendentemente dalla provenienza dell'input, il progetto implementa semplicemente queste azioni come "operazioni da eseguire" o "interagire con" nelle scene.

Per creare una nuova azione di input, è sufficiente fare clic sul pulsante "Aggiungi una nuova azione" e immettere un nome descrittivo per il valore che rappresenta. È quindi necessario solo selezionare un asse (il tipo di dati) che l'azione deve fornire o, nel caso di controller fisici, il tipo di input fisico a cui è possibile collegarsi, ad esempio:

| Vincolo asse | Tipo di dati | Descrizione | Esempio di utilizzo |
| :--- | :--- | :--- | :--- |
| nessuno | Nessun dato | Usato per un'azione o un evento vuoto | Trigger evento |
| RAW (riservato) | object | Riservate per utilizzo futuro | N/D |
| Digitale | bool | Un valore booleano per i dati di tipo | Pulsante controller |
| Asse singolo | float | Un singolo valore di dati di precisione | Un input con intervallo, ad esempio un trigger |
| Asse doppio | Vector2 | Data di tipo float doppio per più assi | DPad o levetta |
| Tre posizioni DOF | Vector3 | Dati di tipo posizionale da con 3 assi a virgola mobile | controller solo stile posizione 3D |
| Rotazione di tre DOF | Quaternion | Input solo rotazionale con 4 assi a virgola mobile | Un controller di stile A tre gradi, ad esempio un controller Oculus go |
| Sei DOF | Pose di realtà mista (Vector3, Quaternion) | Input di tipo posizione e rotazione con i componenti Vector3 e Quaternion | Un controller di movimento o un puntatore |

Gli eventi che utilizzano azioni di input non sono limitati ai controller fisici e possono comunque essere utilizzati all'interno del progetto affinché gli effetti di runtime generino nuove azioni.

> [!NOTE]
> Le azioni di input sono uno dei pochi componenti che non sono modificabili in fase di esecuzione, bensì una configurazione in fase di progettazione. Questo profilo non deve essere scambiato mentre il progetto è in esecuzione a causa della dipendenza del Framework (e dei progetti) nell'ID generato per ogni azione.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionsProfile.png" width="650px" alt="Input Action profile" style="display:block;">

---
<a name="inputactionrules"></a>

## <a name="input-actions-rules"></a>Regole azioni di input

Le regole di azione di input consentono di convertire automaticamente un evento generato per un'azione di input in in azioni diverse in base al relativo valore di dati. Questi vengono gestiti senza problemi all'interno del Framework e non comportano costi di prestazioni.

Ad esempio, la conversione del singolo evento di input a doppio asse da un DPad in alle 4 azioni corrispondenti "DPad UP"/"DPad Down"/"DPad left"/"DPad Right", come illustrato nell'immagine seguente.

Questa operazione può essere eseguita anche nel codice personalizzato. Tuttavia, visto che si tratta di un modello molto comune, il Framework fornisce un meccanismo per eseguire questa operazione "predefinita".

Le regole di azione di input possono essere configurate per uno qualsiasi degli assi di input disponibili. Tuttavia, le azioni di input da un tipo di asse possono essere convertite in un'altra azione di input dello stesso tipo di asse. È possibile eseguire il mapping di un'azione a doppio asse a un'altra azione a due assi, ma non a un'azione digitale o nessuna.

![Profilo delle regole di azione di input](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionRulesProfile.png)

---
<a name="pointer"></a>

## <a name="pointer-configuration"></a>Configurazione puntatore

I puntatori vengono usati per guidare l'interattività nella scena da qualsiasi dispositivo di input, assegnando una direzione e un hit test a qualsiasi oggetto in una scena (con un Collider collegato o è un componente dell'interfaccia utente). Per impostazione predefinita, i puntatori sono configurati automaticamente per i controller, le cuffie (sguardo/stato attivo) e l'input del mouse/tocco.

I puntatori possono anche essere visualizzati all'interno della scena attiva usando uno dei molti componenti linea forniti dal Toolkit di realtà mista o uno dei propri se implementano l'interfaccia IMixedRealityPointer di MRTK.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputPointerProfile.png" width="650px" alt="Pointer configuration" style="display:block;">

- Extent di puntamento: determina l'extent di puntamento globale per tutti i puntatori, incluso lo sguardo.
- Pointing Raycast layer masks: determina a quali puntatori si raycast.
- Debug di disegni che puntano raggi: un helper di debug per la visualizzazione dei raggi usati per Raycasting.
- Disegni di debug che puntano i colori: un set di colori da usare per la visualizzazione.
- Precostruzione del cursore di sguardi: consente di specificare facilmente un cursore globale di sguardi per qualsiasi scena.

È disponibile un pulsante Helper aggiuntivo che consente di passare rapidamente al provider di sguardi per eseguire l'override di alcuni valori specifici per lo sguardo, se necessario.

---
<a name="gestures"></a>

## <a name="gestures-configuration"></a>Configurazione di movimenti

I movimenti sono un'implementazione specifica del sistema che consente di assegnare azioni di input ai vari metodi di input "movimento" forniti da vari SDK (ad esempio HoloLens).

> [!NOTE]
> L'implementazione dei movimenti correnti è solo per il HoloLens e verrà migliorata per gli altri sistemi Man mano che vengono aggiunti al Toolkit in futuro (nessuna data ancora).

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_GesturesProfile.png" width="650px" alt="Gesture Configuration" style="display:block;">

---
<a name="speech"></a>

## <a name="speech-commands"></a>Comandi vocali

Analogamente ai movimenti, alcune piattaforme di runtime forniscono anche una funzionalità intelligente di riconoscimento vocale con la possibilità di generare comandi che possono essere ricevuti da un progetto Unity. Questo profilo di configurazione consente di configurare quanto segue:

1. Impostazioni generali: "avvia comportamento" impostato su avvio automatico o avvio manuale determina se inizializzare KeywordRecognizer all'avvio del sistema di input o lasciare che il progetto decida quando inizializzare il KeywordRecognizer. "Livello di confidenza del riconoscimento" viene usato per inizializzare l' [API KeywordRecognizer](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html) di Unity
2. Comandi vocali: registra "Words" e li converte in azioni di input che possono essere ricevute dal progetto. Possono anche essere collegati alle azioni della tastiera, se necessario.

> [!IMPORTANT]
> Il sistema supporta attualmente solo il riconoscimento vocale quando viene eseguito su piattaforme Windows 10, ad esempio HoloLens e Windows 10 desktop e sarà migliorato per altri sistemi Man mano che vengono aggiunti a MRTK in futuro (nessuna data).

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpeechCommandsProfile.png" width="650px" alt="Speech command profile" style="display:block;">

---
<a name="mapping"></a>

## <a name="controller-mapping-configuration"></a>Configurazione mapping controller

Una delle schermate di configurazione principali per il Toolkit di realtà mista è la possibilità di configurare ed eseguire il mapping dei vari tipi di controller che possono essere utilizzati dal progetto.

La schermata di configurazione seguente consente di configurare i controller attualmente riconosciuti dal Toolkit.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerMappingProfile.png" width="650px" alt="Controller mapping profiler" style="display:block;">

MRTK fornisce una configurazione predefinita per i controller/sistemi seguenti:

- Mouse (incluso il supporto del mouse spaziale 3D)
- Touch screen
- Controller Xbox
- Controller della realtà mista di Windows
- Movimenti HoloLens
- Controller della bacchetta HTC vive
- Controller Oculus touch
- Controller remoto Oculus
- Dispositivi OpenVR generici (solo utenti avanzati)

Facendo clic sull'immagine per uno dei sistemi controller predefiniti è possibile configurare una singola azione di input per tutti gli input corrispondenti. ad esempio, vedere la schermata di configurazione di Oculus touch controller riportata di seguito:

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_WindowsMixedRealityControllerConfigScreen.png" width="650px" alt="Controller configuration screen" style="display:block;">

È disponibile anche una schermata avanzata per la configurazione di altri controller di input OpenVR o Unity che non sono stati identificati in precedenza.

---
<a name="visualization"></a>

## <a name="controller-visualization-settings"></a>Impostazioni di visualizzazione del controller

Oltre al mapping del controller, viene fornito un profilo di configurazione separato per personalizzare il modo in cui vengono presentati i controller all'interno delle scene.

Questa operazione può essere configurata in un "globale" (tutte le istanze di un controller per una specifica mano) o specifica per un singolo tipo di controller/mano.

MRTK supporta anche modelli di controller SDK nativi per la realtà mista di Windows e OpenVR. Questi vengono caricati come GameObject nella scena e posizionati usando il rilevamento del controller della piattaforma.

Se la rappresentazione del controller nella scena deve essere sottoposta a offset dalla posizione del controller fisico, è sufficiente impostare tale offset rispetto al prefabbricato del modello del controller (ad esempio, impostando la posizione di trasformazione del prefabbricato del controller con una posizione di offset).

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerVisualizationProfile.png" width="650px" alt="Cotroller visualization" style="display:block;">

<a name="editor-utilities"></a>

## <a name="editor-utilities"></a>Utilità Editor

Le utilità seguenti funzionano solo nell'editor e sono utili per migliorare la produttività dello sviluppo.

![Utilità di configurazione dell'editor MRTK](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_EditorConfiguration.png)

### <a name="service-inspectors"></a>Controlli servizio

I controlli servizio sono una funzionalità di solo editor che genera oggetti in scena che rappresentano servizi attivi. Selezionando questi oggetti vengono visualizzati i controlli che offrono collegamenti alla documentazione, il controllo sulle visualizzazioni dell'editor e informazioni dettagliate sullo stato del servizio.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ServiceInspectors.PNG" width="350px" alt="Service Inspector" style="display:block;">

È possibile abilitare gli ispettori dei servizi controllando *Usa controlli servizio* in *Impostazioni editor* nel profilo di configurazione.

### <a name="depth-buffer-renderer"></a>Renderer buffer profondità

La condivisione del buffer di profondità con alcune piattaforme di realtà miste può migliorare la [stabilizzazione di ologrammi](../performance/hologram-stabilization.md). La piattaforma per la realtà mista di Windows, ad esempio, può modificare la scena di cui è stato eseguito il rendering per ogni pixel per tenere conto dei movimenti di intestazioni sottili durante il tempo impiegato per il rendering del frame. Tuttavia, queste tecniche richiedono buffer di profondità con dati accurati per individuare la posizione e la distanza di geometria dall'utente.

Per assicurarsi che una scena esegua il rendering di tutti i dati necessari nel buffer di profondità, gli sviluppatori possono abilitare o disabilitare la funzionalità di *buffer di profondità di rendering* in *Impostazioni editor* nel profilo di configurazione. Questa operazione condurrà il buffer di profondità corrente e ne eseguirà il rendering come colore nella visualizzazione della scena applicando un effetto di post-elaborazione, [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer) , alla fotocamera principale.

![Utilità del buffer di profondità ](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
 <sup>di rendering il cilindro blu nella scena ha un materiale con ZWrite off, quindi non viene scritto alcun dato di profondità</sup>

## <a name="changing-profiles-at-runtime"></a>Modifica dei profili in fase di esecuzione

È possibile aggiornare i profili in fase di esecuzione e in genere esistono due diversi scenari e tempi in cui questo è utile:

1. All'avvio, prima dell'inizializzazione di MRTK, lo scambio del profilo per abilitare o disabilitare funzionalità diverse in base alle funzionalità del dispositivo. Se, ad esempio, l'esperienza viene eseguita in VR senza hardware per il mapping spaziale, probabilmente non ha senso avere un componente di mapping spaziale abilitato.
1. Dopo l'avvio, dopo l'inizializzazione di MRTK, lo scambio del profilo per modificare la modalità di funzionamento di determinate funzionalità. È ad esempio possibile che nell'applicazione sia presente un'esperienza secondaria specifica che desidera che i puntatori a distanza siano completamente rimossi. **Si noti** che questo tipo di scambio attualmente non funziona a causa di questo [problema](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/4289):

## <a name="swapping-profiles-prior-to-mrtk-initialization"></a>Scambio di profili prima dell'inizializzazione di MRTK

Questa operazione può essere eseguita connettendo un monocomportamento (esempio riportato di seguito) che viene eseguito prima dell'inizializzazione di MRTK:

```csharp
using Microsoft.MixedReality.Toolkit;
using UnityEditor;
using UnityEngine;

/// <summary>
/// Sample MonoBehaviour that will run before the MixedRealityToolkit object, and change
/// the profile, so that when the MRTK initializes it uses the profile specified below
/// rather than the one that is saved in its scene.
/// </summary>
/// <remarks>
/// Note that this script must have a higher priority in the script execution order compared
/// to that of MixedRealityToolkit.cs. See https://docs.unity3d.com/Manual/class-MonoManager.html
/// for more information on script execution order.
/// </remarks>
public class ProfileSwapper : MonoBehaviour
{
    void Start()
    {
        // Here you could choose any arbitrary MixedRealityToolkitConfigurationProfile (for example, you could
        // add some platform checking code here to determine which profile to load).
        var profile = AssetDatabase.LoadAssetAtPath<MixedRealityToolkitConfigurationProfile>("Assets/MixedRealityToolkit.Generated/CustomProfiles/RuntimeSwapparoo.asset");
        MixedRealityToolkit.Instance.ActiveProfile = profile;
    }
}
```

Anziché "RuntimeSwapparoo. asset", è possibile avere un set arbitrario di profili che si applicano a piattaforme specifiche, ad esempio una per HoloLens 1, una per VR, una per HoloLens 2 e così via. È possibile usare diversi altri [indicatori](https://docs.unity3d.com/ScriptReference/SystemInfo.html)o se la fotocamera è opaca o trasparente) per individuare il profilo da caricare.

## <a name="see-also"></a>Vedi anche

- [Stabilizzazione ologramma](../performance/hologram-stabilization.md)
