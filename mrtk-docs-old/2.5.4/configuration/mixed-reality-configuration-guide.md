---
title: MixedRealityConfigurationGuide
description: Documentazione per configurare MRTK in Unity.
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 51ce04fd1ebae24ff709d70def2ec7a5057e105166d765eb0137553dddee8f54
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189376"
---
# <a name="mixed-reality-toolkit-profile-configuration-guide"></a>Guida alla configurazione Toolkit profilo di realtà mista

![Logo di MRTK](../features/images/MRTK_Logo_Rev.png)

L'Toolkit realtà mista centralizza la maggior parte della configurazione necessaria per gestire il toolkit ( ad eccezione dei veri "cose" di runtime).

Questa guida è una procedura dettagliata semplice per ognuna delle schermate del profilo di configurazione attualmente disponibili per il toolkit.

## <a name="the-main-mixed-reality-toolkit-configuration-profile"></a>Profilo di configurazione principale Toolkit realtà mista

Il profilo di configurazione principale, collegato al GameObject *MixedRealityToolkit* nella scena, fornisce il punto di ingresso principale per il Toolkit nel progetto.

> [!NOTE]
> L'Toolkit realtà mista "blocca" le schermate di configurazione predefinite per assicurarsi di avere sempre un punto di partenza comune per il progetto ed è consigliato iniziare a definire impostazioni personalizzate con l'evolversi del progetto. La configurazione di MRTK non è modificabile durante la modalità di riproduzione.

![Profilo di configurazione di MRTK](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ActiveConfiguration.png)

Tutti i profili "predefiniti" per l'Toolkit realtà mista sono disponibili nel progetto SDK nella cartella Assets/MRTK/SDK/Profiles.

> [!IMPORTANT]
> DefaultHoloLens2ConfigurationProfile è ottimizzato per HoloLens 2. Per [informazioni dettagliate,](../features/profiles/profiles.md) vedere Profili.

Quando si apre il profilo di configurazione Toolkit realtà mista principale, verrà visualizzata la schermata seguente nel controllo:

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_MixedRealityToolkitConfigurationScreen.png" width="650px" alt="MRTK configuration scene" style="display:block;">

Se si seleziona un asset MixedRealityToolkitConfigurationProfile senza MixedRealityToolkit nella scena, verrà chiesto se si vuole che MRTK configura automaticamente la scena. Questo è facoltativo, tuttavia, deve essere presente un oggetto MixedRealityToolkit attivo nella scena per accedere a tutte le schermate di configurazione.

In questo modo viene ospitata la configurazione di runtime attiva corrente per il progetto.

Da qui è possibile passare a tutti i profili di configurazione per MRTK, tra cui:

- [Guida alla configurazione Toolkit profilo di realtà mista](#mixed-reality-toolkit-profile-configuration-guide)
  - [Profilo di configurazione principale Toolkit realtà mista](#the-main-mixed-reality-toolkit-configuration-profile)
  - [Impostazioni dell'esperienza](#experience-settings)
  - [Impostazioni della fotocamera](#camera-settings)
  - [Impostazioni di sistema di input](#input-system-settings)
  - [Impostazioni di visualizzazione dei limiti](#boundary-visualization-settings)
  - [Selezione del sistema di teletrasporto](#teleportation-system-selection)
  - [Impostazioni di consapevolezza spaziale](#spatial-awareness-settings)
  - [Impostazioni di diagnostica](#diagnostics-settings)
  - [Impostazioni di sistema della scena](#scene-system-settings)
  - [Impostazioni dei servizi aggiuntivi](#additional-services-settings)
  - [Impostazioni delle azioni di input](#input-actions-settings)
  - [Regole delle azioni di input](#input-actions-rules)
  - [Configurazione del puntatore](#pointer-configuration)
  - [Configurazione dei movimenti](#gestures-configuration)
  - [Comandi vocali](#speech-commands)
  - [Configurazione del mapping del controller](#controller-mapping-configuration)
  - [Impostazioni di visualizzazione del controller](#controller-visualization-settings)
  - [Utilità dell'editor](#editor-utilities)
    - [Controlli dei servizi](#service-inspectors)
    - [Renderer del buffer di profondità](#depth-buffer-renderer)
  - [Modifica dei profili in fase di esecuzione](#changing-profiles-at-runtime)
  - [Scambio di profili prima dell'inizializzazione di MRTK](#swapping-profiles-prior-to-mrtk-initialization)
  - [Vedere anche](#see-also)

Questi profili di configurazione sono riportati di seguito nelle sezioni pertinenti:

---
<a name="experience"></a>

## <a name="experience-settings"></a>Impostazioni dell'esperienza

Disponibile nella pagina principale di configurazione Toolkit realtà mista, questa impostazione definisce il funzionamento predefinito della scalabilità dell'ambiente di realtà [mista](https://docs.microsoft.com/windows/mixed-reality/coordinate-systems-in-unity) per il progetto.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ExperienceSettings.png" width="650px" alt="Experiance settings" style="display:block;">

---
<a name="camera"></a>

## <a name="camera-settings"></a>Impostazioni della fotocamera

Le impostazioni della fotocamera definiscono come verrà impostata la fotocamera per il progetto di realtà mista, definendo le impostazioni generiche di ritaglio, qualità e trasparenza.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_CameraProfile.png" width="650px" alt="Camera Profile" style="display:block;">

---
<a name="inputsystem"></a>

## <a name="input-system-settings"></a>Impostazioni del sistema di input

L'Project realtà mista offre un sistema di input affidabile e ben formato per il routing di tutti gli eventi di input intorno al progetto selezionato per impostazione predefinita.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemSelection.png" width="650px" alt="Input System settings 1" style="display:block;">

Dietro il sistema di input fornito da MRTK ci sono diversi altri sistemi, che consentono di gestire le complesse inter-tessere necessarie per astrarre le complessità di un framework multipiattaforma/realtà mista.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemProfile.png" width="650px" alt="Input System settings 2" style="display:block;">

Ognuno dei singoli profili è descritto in dettaglio di seguito:

- Stato attivo Impostazioni
- [Impostazioni delle azioni di input](#input-actions-settings)
- [Regole delle azioni di input](#input-actions-rules)
- [Configurazione del puntatore](#pointer-configuration)
- [Configurazione dei movimenti](#gestures-configuration)
- [Comandi vocali](#speech-commands)
- [Configurazione del mapping del controller](#controller-mapping-configuration)
- [Impostazioni di visualizzazione del controller](#controller-visualization-settings)

---
<a name="boundary"></a>

## <a name="boundary-visualization-settings"></a>Impostazioni di visualizzazione dei limiti

Il sistema di limiti trasla il limite percepito segnalato dal sistema limite/guardiano delle piattaforme sottostanti. La configurazione del visualizzatore di limiti consente di visualizzare automaticamente il limite registrato all'interno della scena rispetto alla posizione dell'utente. Il limite reagirà o si aggiornerà anche in base alla posizione in cui l'utente si teletrasporta all'interno della scena.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_BoundaryVisualizationProfile.png" width="650px" alt="Boundry Visualization Settings" style="display:block;">

---
<a name="teleportation"></a>

## <a name="teleportation-system-selection"></a>Selezione del sistema di teletrasporto

L'Project realtà mista offre un sistema di teletrasporto completo per la gestione degli eventi di teletrasporto nel progetto, selezionato per impostazione predefinita.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_TeleportationSystemSelection.png" width="650px" alt="Teleport System settings" style="display:block;">

---
<a name="spatialawareness"></a>

## <a name="spatial-awareness-settings"></a>Impostazioni di consapevolezza spaziale

L'Project realtà mista offre un sistema di consapevolezza spaziale ricompilato per l'uso di sistemi di analisi spaziale nel progetto, selezionato per impostazione predefinita.
È possibile visualizzare l'architettura alla base del sistema di consapevolezza [spaziale MRTK qui](../architecture/spatial-awareness.md).

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessSystemSelection.png" width="650px" alt="Spatial Awareness settings 1" style="display:block;">

La configurazione di consapevolezza spaziale Toolkit realtà mista consente di personalizzare la modalità di avvio del sistema, sia che sia automatica all'avvio dell'applicazione o in un secondo momento a livello di codice, nonché di impostare gli extent per il campo di visualizzazione.

Consente anche di configurare le impostazioni della mesh e della superficie, personalizzando ulteriormente il modo in cui il progetto comprende l'ambiente intorno all'utente.

Questo è applicabile solo per i dispositivi che possono fornire un ambiente analizzato.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessProfile.png" width="650px" alt="Spatial Awareness settings 2" style="display:block;">

---
<a name="diagnostic"></a>

## <a name="diagnostics-settings"></a>Impostazioni di diagnostica

Una funzionalità facoltativa ma estremamente utile di MRTK è la funzionalità di diagnostica del plug-in.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsSystemSelection.png" width="650px" alt="Diagnostics settings" style="display:block;">

Il profilo di diagnostica fornisce diversi sistemi semplici da monitorare durante l'esecuzione del progetto, tra cui un pratico interruttore On/Off per abilitare/disabilitare il pannello di visualizzazione nella scena.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsProfile.png" width="650px" alt="Diagnostics settings System settings 2" style="display:block;">

---
<a name="scenesystem"></a>

## <a name="scene-system-settings"></a>Impostazioni di sistema della scena

MRTK fornisce questo servizio facoltativo che consente di gestire il caricamento/scaricamento di scene additive complesse. Per decidere se il sistema della scena è una scelta adatta al progetto, leggi la Guida al sistema [Attività iniziali scena.](../features/scene-system/scene-system-getting-started.md)

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SceneSystemProfile.png" width="650px" alt="Scene System settings 1" style="display:block;">

---
<a name="services"></a>

## <a name="additional-services-settings"></a>Impostazioni dei servizi aggiuntivi

Una delle aree più avanzate di Mixed Reality [](https://en.wikipedia.org/wiki/Service_locator_pattern) Toolkit è l'implementazione del modello di localizzatore di servizi che consente la registrazione di qualsiasi "servizio" con il framework. In questo modo il framework può essere esteso con facilità con nuove funzionalità/sistemi, ma consente anche ai progetti di sfruttare queste funzionalità per registrare i propri componenti di runtime.

Qualsiasi servizio registrato ottiene comunque il vantaggio completo di tutti gli eventi unity, senza il sovraccarico e il costo dell'implementazione di modelli singleton MonoBehaviour o clunky. Ciò consente componenti C# puri senza overhead della scena per l'esecuzione di processi in primo piano e in background, ad esempio sistemi di generazione, logica di gioco di runtime o praticamente qualsiasi altro elemento.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_RegisteredServiceProvidersProfile.png" width="650px" alt="additional System settings" style="display:block;">

---
<a name="inputactions"></a>

## <a name="input-actions-settings"></a>Impostazioni delle azioni di input

Le azioni di input consentono di astrarre eventuali interazioni fisiche e input da un progetto di runtime. Tutto l'input fisico (da controller/mani/mouse/e così via) viene convertito in un'azione di input logica da usare nel progetto di runtime. In questo modo, indipendentemente dall'origine dell'input, il progetto implementa semplicemente queste azioni come "Cose da fare" o "Interagisci" nelle scene.

Per creare una nuova azione di input, è sufficiente fare clic sul pulsante "Aggiungi una nuova azione" e immettere un nome di testo descrittivo per ciò che rappresenta. È quindi necessario selezionare solo un asse (il tipo di dati) a cui l'azione deve comunicare o, nel caso dei controller fisici, il tipo di input fisico a cui può essere collegata, ad esempio:

| Vincolo dell'asse | Tipo di dati | Descrizione | Esempio d'uso |
| :--- | :--- | :--- | :--- |
| Nessuno | Nessun dato | Usato per un'azione o un evento vuoto | Trigger di evento |
| Non elaborato (riservato) | object | Riservate per utilizzo futuro | N/D |
| Digitale | bool | Dati di tipo booleano on o off | Un pulsante del controller |
| Asse singolo | float | Un singolo valore di dati di precisione | Un input con intervallo, ad esempio un trigger |
| Asse doppio | Vector2 | Data di tipo float doppia per più assi | Un Dpad o una levetta |
| Posizione tre Dof | Vector3 | Dati di tipo posizionale da con 3 assi float | Controller solo stile di posizione 3D |
| Rotazione di tre Dof | Quaternion | Input solo rotazionale con 4 assi float | Un controller di tipo Tre gradi, ad esempio controller Oculus Go |
| Sei Dof | Posizione in realtà mista (Vector3, Quaternion) | Input dello stile di posizione e rotazione con componenti Vector3 e Quaternion | Un controller del movimento o un puntatore |

Gli eventi che utilizzano azioni di input non sono limitati ai controller fisici e possono comunque essere utilizzati all'interno del progetto per fare in modo che gli effetti di runtime generino nuove azioni.

> [!NOTE]
> Le azioni di input sono uno dei pochi componenti non modificabili in fase di esecuzione, ma solo una configurazione in fase di progettazione. Questo profilo non deve essere scambiato mentre il progetto è in esecuzione a causa della dipendenza del framework (e dei progetti) dall'ID generato per ogni azione.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionsProfile.png" width="650px" alt="Configuration Profile" style="display:block;">

---
<a name="inputactionrules"></a>

## <a name="input-actions-rules"></a>Regole delle azioni di input

Le regole di azione di input consentono di convertire automaticamente un evento generato per un'azione di input in azioni diverse in base al valore dei dati. Questi vengono gestiti senza problemi all'interno del framework e non comportano costi per le prestazioni.

Ad esempio, la conversione del singolo evento di input doppio asse da un DPad in alle 4 azioni corrispondenti "Dpad Up" / "DPad Down" / "Dpad Left" / "Dpad Right" (come illustrato nell'immagine seguente).

Questa operazione può essere eseguita anche nel codice. Tuttavia, poiché si tratta di un modello molto comune, il framework fornisce un meccanismo per eseguire questa operazione "predefinita"

Le regole dell'azione di input possono essere configurate per qualsiasi asse di input disponibile. Tuttavia, le azioni di input da un tipo di asse possono essere convertite in un'altra azione di input dello stesso tipo di asse. È possibile eseguire il mapping di un'azione asse doppio a un'altra azione asse doppio, ma non a un'azione digitale o nessuna azione.

![Profilo delle regole di azione di input](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionRulesProfile.png)

---
<a name="pointer"></a>

## <a name="pointer-configuration"></a>Configurazione del puntatore

I puntatori vengono usati per guidare l'interattività nella scena da qualsiasi dispositivo di input, fornendo sia una direzione che un hit test con qualsiasi oggetto in una scena (che ha un collisore collegato o è un componente dell'interfaccia utente). Per impostazione predefinita, i puntatori vengono configurati automaticamente per controller, visori VR (sguardo fisso/messa a fuoco) e input tramite mouse/tocco.

I puntatori possono anche essere visualizzati all'interno della scena attiva usando uno dei numerosi componenti linea forniti dal Toolkit di realtà mista o uno dei propri se implementano l'interfaccia IMixedRealityPointer di MRTK.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputPointerProfile.png" width="650px" alt="Input Pointer Profile" style="display:block;">

- Extent di puntamento: determina l'extent di puntamento globale per tutti i puntatori, incluso lo sguardo fisso.
- Raycast Layer Masks (Maschera livello raycast di puntamento): determina su quali puntatori di livelli verrà esere il raycast.
- Debug dei raggi di puntamento di disegno: helper di debug per la visualizzazione dei raggi usati per il raycasting.
- Eseguire il debug dei colori dei raggi di disegno: set di colori da usare per la visualizzazione.
- Prefab cursore sguardo fisso: consente di specificare facilmente un cursore di sguardo fisso globale per qualsiasi scena.

È presente un pulsante helper aggiuntivo per passare rapidamente al provider di sguardo fisso per eseguire l'override di alcuni valori specifici per Sguardo fisso, se necessario.

---
<a name="gestures"></a>

## <a name="gestures-configuration"></a>Configurazione dei movimenti

I movimenti sono un'implementazione specifica del sistema che consente di assegnare azioni di input ai vari metodi di input "Movimento" forniti da vari SDK ,ad esempio HoloLens.

> [!NOTE]
> L'implementazione corrente di Gestures è solo per il HoloLens e verrà migliorata per gli altri sistemi poiché verranno aggiunti al Toolkit in futuro (nessuna data ancora).

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_GesturesProfile.png" width="650px" alt="Gesture configuration" style="display:block;">

---
<a name="speech"></a>

## <a name="speech-commands"></a>Comandi vocali

Analogamente ai movimenti, alcune piattaforme di runtime forniscono anche funzionalità intelligenti di Riconoscimento vocale con la possibilità di generare comandi che possono essere ricevuti da un progetto Unity. Questo profilo di configurazione consente di configurare quanto segue:

1. General Impostazioni - "Start Behavior" (Comportamento di avvio) impostato su Auto Start (Avvio automatico) o Manual Start (Avvio manuale) determina se inizializzare KeywordRecognizer all'avvio del sistema di input o lasciare che il progetto decida quando inizializzare KeywordRecognizer. Il "livello di attendibilità del riconoscimento" viene usato per inizializzare [l'API KeywordRecognizer di Unity](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html)
2. Comandi vocali: registra le "parole" e le converte in azioni di input che possono essere ricevute dal progetto. Possono anche essere collegati alle azioni della tastiera, se necessario.

> [!IMPORTANT]
> Il sistema attualmente supporta il riconoscimento vocale solo in caso di esecuzione su piattaforme Windows 10, ad esempio HoloLens e Windows 10 Desktop, e verrà migliorato per altri sistemi, perché verranno aggiunti a MRTK in futuro (nessuna data ancora).

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpeechCommandsProfile.png" width="650px" alt="Configuration Profile screens" style="display:block;">

---
<a name="mapping"></a>

## <a name="controller-mapping-configuration"></a>Configurazione del mapping del controller

Una delle schermate di configurazione di base per Mixed Reality Toolkit è la possibilità di configurare ed eseguire il mapping dei vari tipi di controller che possono essere utilizzati dal progetto.

La schermata di configurazione seguente consente di configurare uno dei controller attualmente riconosciuti dal toolkit.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerMappingProfile.png" width="650px" alt="Controller Mapping" style="display:block;">

MRTK fornisce una configurazione predefinita per i controller/sistemi seguenti:

- Mouse (incluso il supporto del mouse spaziale 3D)
- Touch screen
- Controller Xbox
- controller Windows Mixed Reality
- HoloLens Gesti
- CONTROLLER DELLA RETE WAND DI VIVE
- Controller Oculus Touch
- Controller remoto Oculus
- Dispositivi OpenVR generici (solo utenti avanzati)

Facendo clic sull'immagine per uno dei sistemi controller predefiniti è possibile configurare una singola azione di input per tutti gli input corrispondenti, ad esempio, vedere la schermata di configurazione del controller Oculus Touch riportata di seguito:

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_WindowsMixedRealityControllerConfigScreen.png" width="650px" alt="Controller config screen" style="display:block;">

È disponibile anche una schermata avanzata per la configurazione di altri controller di input OpenVR o Unity non identificati in precedenza.

---
<a name="visualization"></a>

## <a name="controller-visualization-settings"></a>Impostazioni di visualizzazione del controller

Oltre al mapping del controller, viene fornito un profilo di configurazione separato per personalizzare il modo in cui i controller vengono presentati all'interno delle scene.

Può essere configurato a livello "globale" (tutte le istanze di un controller per una mano specifica) o specifico per un singolo tipo di controller/mano.

MRTK supporta anche modelli di controller SDK nativi per Windows Mixed Reality e OpenVR. Questi vengono caricati come GameObject nella scena e posizionati usando il monitoraggio del controller della piattaforma.

Se la rappresentazione del controller nella scena deve essere offset dalla posizione fisica del controller, è sufficiente impostare tale offset rispetto al prefab del modello controller (ad esempio, impostando la posizione di trasformazione del prefab controller con una posizione di offset).

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerVisualizationProfile.png" width="650px" alt="Visualization profile" style="display:block;">

<a name="editor-utilities"></a>

## <a name="editor-utilities"></a>Utilità dell'editor

Le utilità seguenti funzionano solo nell'editor e sono utili per migliorare la produttività di sviluppo.

![Utilità di configurazione dell'editor MRTK](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_EditorConfiguration.png)

### <a name="service-inspectors"></a>Controlli dei servizi

I controlli dei servizi sono una funzionalità solo editor che genera oggetti nella scena che rappresentano i servizi attivi. Selezionando questi oggetti vengono visualizzati controlli che offrono collegamenti alla documentazione, controllo sulle visualizzazioni dell'editor e informazioni dettagliate sullo stato del servizio.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ServiceInspectors.PNG" width="350px" alt="Service Inspectors" style="display:block;">

È possibile abilitare i controlli dei servizi selezionando *Use Service Inspectors* (Usa controlli servizio) in *Editor Impostazioni* nel profilo di configurazione.

### <a name="depth-buffer-renderer"></a>Renderer buffer di profondità

La condivisione del buffer di profondità con alcune piattaforme di realtà mista può migliorare [la stabilizzazione dell'ologramma.](../performance/hologram-stabilization.md) Ad esempio, la piattaforma Windows Mixed Reality può modificare la scena di cui è stato eseguito il rendering per pixel per rendere conto dei movimenti della testa durante il tempo necessario per il rendering di un fotogramma. Tuttavia, queste tecniche richiedono buffer di profondità con dati accurati per sapere dove e quanto è distante la geometria dall'utente.

Per assicurarsi che una scena eserciti il rendering di tutti i dati necessari nel buffer di profondità, gli sviluppatori possono attivare o disattivare la funzionalità *Buffer* profondità di rendering in *Editor Impostazioni* nel profilo di configurazione. In questo modo il buffer di profondità corrente verrà visualizzato come colore per la visualizzazione della scena applicando un effetto di post-elaborazione, [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer) , alla fotocamera principale.

![Utilità buffer di profondità di rendering Il cilindro blu nella scena ha un materiale con ](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
 <sup>ZWrite disattivato,</sup> quindi non vengono scritti dati di profondità

## <a name="changing-profiles-at-runtime"></a>Modifica dei profili in fase di esecuzione

È possibile aggiornare i profili in fase di esecuzione e in genere esistono due scenari e momenti diversi in cui ciò risulta utile:

1. All'avvio, prima dell'inizializzazione di MRTK, lo scambio del profilo per abilitare/disabilitare funzionalità diverse in base alle funzionalità del dispositivo. Ad esempio, se l'esperienza è in esecuzione nella realtà virtuale che non dispone di hardware di mapping spaziale, probabilmente non ha senso avere il componente di mapping spaziale abilitato.
1. Dopo l'avvio, dopo l'inizializzazione di MRTK, lo scambio del profilo cambia il comportamento di determinate funzionalità. Ad esempio, potrebbe esserci un'esperienza secondaria specifica nell'applicazione che vuole rimuovere completamente i puntatori a mano da lontano. **Si** noti che questo tipo di scambio attualmente non funziona a causa di questo problema: [https://github.com/microsoft/MixedRealityToolkit-Unity/issues/4289](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/4289) .

## <a name="swapping-profiles-prior-to-mrtk-initialization"></a>Scambio di profili prima dell'inizializzazione di MRTK

Questa operazione può essere eseguita collegando un oggetto MonoBehaviour (esempio seguente) che viene eseguito prima dell'inizializzazione di MRTK:

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

Invece di "RuntimeSwapparoo.asset", è possibile avere un set arbitrario di profili che si applicano a piattaforme specifiche (ad esempio, uno per HoloLens 1, uno per la realtà virtuale, uno per HoloLens 2 e così via). È possibile usare vari altri indicatori (ad esempio , o se la fotocamera è opaca/trasparente) per determinare il profilo [https://docs.unity3d.com/ScriptReference/SystemInfo.html](https://docs.unity3d.com/ScriptReference/SystemInfo.html) da caricare.

## <a name="see-also"></a>Vedi anche

- [Stabilizzazione dell'ologramma](../performance/hologram-stabilization.md)
