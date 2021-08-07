---
title: Guida alla configurazione del profilo MRTK
description: Documentazione per configurare MRTK in Unity.
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: e18695610b5e07c4f811e7c43bc13607857a9459407f9b16f39d4f7350f354e6
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214924"
---
# <a name="mrtk-profile-configuration-guide"></a>Guida alla configurazione del profilo MRTK

L'Toolkit realtà mista centralizza la maggior parte della configurazione necessaria per gestire il toolkit (ad eccezione dei veri "elementi" di runtime).

Questa guida è una procedura dettagliata semplice per ognuna delle schermate del profilo di configurazione attualmente disponibili per il toolkit.

## <a name="the-main-mixed-reality-toolkit-configuration-profile"></a>Profilo di configurazione Toolkit realtà mista principale

Il profilo di configurazione principale, collegato a *MixedRealityToolkit* GameObject nella scena, fornisce il punto di ingresso principale per il Toolkit nel progetto.

> [!NOTE]
> La realtà mista Toolkit "blocca" le schermate di configurazione predefinite per assicurarsi di avere sempre un punto di partenza comune per il progetto ed è consigliato iniziare a definire le proprie impostazioni con l'evolversi del progetto. La configurazione di MRTK non è modificabile durante la modalità di riproduzione.

![Profilo di configurazione MRTK](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ActiveConfiguration.png)

Tutti i profili "predefiniti" per Toolkit realtà mista sono disponibili nel progetto SDK nella cartella Assets/MRTK/SDK/Profiles.

> [!IMPORTANT]
> DefaultHoloLens2ConfigurationProfile è ottimizzato per HoloLens 2. Per [informazioni dettagliate,](../features/profiles/profiles.md) vedere Profili.

Quando si apre il profilo di configurazione Toolkit realtà mista principale, nel controllo verrà visualizzata la schermata seguente:

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_MixedRealityToolkitConfigurationScreen.png" width="650px" alt="MRTK configuration scene" style="display:block;">

Se si seleziona un asset MixedRealityToolkitConfigurationProfile senza MixedRealityToolkit nella scena, verrà chiesto se si vuole che MRTK configura automaticamente la scena. Questo è facoltativo, tuttavia, deve essere presente un oggetto MixedRealityToolkit attivo nella scena per accedere a tutte le schermate di configurazione.

In questo modo viene ospitata la configurazione di runtime attiva corrente per il progetto.

Da qui è possibile passare a tutti i profili di configurazione per MRTK, tra cui:

- [Guida alla configurazione Toolkit profilo di realtà mista](#mrtk-profile-configuration-guide)
  - [Profilo di configurazione Toolkit realtà mista principale](#the-main-mixed-reality-toolkit-configuration-profile)
  - [Impostazioni dell'esperienza](#experience-settings)
  - [Impostazioni della fotocamera](#camera-settings)
  - [Impostazioni di sistema di input](#input-system-settings)
  - [Impostazioni di visualizzazione dei limiti](#boundary-visualization-settings)
  - [Selezione del sistema di teletrasporto](#teleportation-system-selection)
  - [Impostazioni di consapevolezza spaziale](#spatial-awareness-settings)
  - [Impostazioni di diagnostica](#diagnostics-settings)
  - [Impostazioni di sistema della scena](#scene-system-settings)
  - [Impostazioni aggiuntive dei servizi](#additional-services-settings)
  - [Impostazioni delle azioni di input](#input-actions-settings)
  - [Regole delle azioni di input](#input-actions-rules)
  - [Configurazione del puntatore](#pointer-configuration)
  - [Configurazione dei movimenti](#gestures-configuration)
  - [Comandi vocali](#speech-commands)
  - [Configurazione del mapping dei controller](#controller-mapping-configuration)
  - [Impostazioni di visualizzazione del controller](#controller-visualization-settings)
  - [Utilità dell'editor](#editor-utilities)
    - [Controlli dei servizi](#service-inspectors)
    - [Renderer del buffer di profondità](#depth-buffer-renderer)
  - [Modifica dei profili in fase di esecuzione](#changing-profiles-at-runtime)
    - [Opzione del profilo di inizializzazione MRTK precedente](#pre-mrtk-initialization-profile-switch)
    - [Opzione del profilo attivo](#active-profile-switch)
  - [Vedere anche](#see-also)

Questi profili di configurazione sono dettagliati di seguito nelle sezioni pertinenti:

---
<a name="experience"></a>

## <a name="experience-settings"></a>Impostazioni dell'esperienza

Nella pagina di configurazione principale Toolkit realtà mista, questa impostazione definisce il funzionamento predefinito della scalabilità dell'ambiente di realtà mista [per](/windows/mixed-reality/coordinate-systems-in-unity) il progetto.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ExperienceSettings.png" width="650px" alt="Experiance settings" style="display:block;">

---
<a name="camera"></a>

## <a name="camera-settings"></a>Impostazioni della fotocamera

Le impostazioni della fotocamera definiscono la modalità di configurazione della fotocamera per il progetto di realtà mista, definendo le impostazioni generiche di ritaglio, qualità e trasparenza.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_CameraProfile.png" width="650px" alt="Camera Profile" style="display:block;">

---
<a name="inputsystem"></a>

## <a name="input-system-settings"></a>Impostazioni di sistema di input

L'Project realtà mista offre un sistema di input affidabile e ben addestrato per il routing di tutti gli eventi di input intorno al progetto selezionato per impostazione predefinita.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemSelection.png" width="650px" alt="Input System settings 1" style="display:block;">

Dietro il sistema di input fornito da MRTK sono presenti diversi altri sistemi, che consentono di gestire e gestire le complesse inter-tessitura necessarie per astrarre le complessità di un framework multipiattaforma/realtà mista.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemProfile.png" width="650px" alt="Input System settings 2" style="display:block;">

Ognuno dei singoli profili è descritto in dettaglio di seguito:

- Concentrarsi Impostazioni
- [Impostazioni delle azioni di input](#input-actions-settings)
- [Regole delle azioni di input](#input-actions-rules)
- [Configurazione del puntatore](#pointer-configuration)
- [Configurazione dei movimenti](#gestures-configuration)
- [Comandi vocali](#speech-commands)
- [Configurazione del mapping dei controller](#controller-mapping-configuration)
- [Impostazioni di visualizzazione del controller](#controller-visualization-settings)

---
<a name="boundary"></a>

## <a name="boundary-visualization-settings"></a>Impostazioni di visualizzazione dei limiti

Il sistema di limiti traduce il limite percepito segnalato dal sistema limite/guardiano delle piattaforme sottostanti. La configurazione del visualizzatore limite consente di visualizzare automaticamente il limite registrato all'interno della scena rispetto alla posizione dell'utente. Il limite reagirà o si aggiornerà anche in base al punto in cui l'utente teletrasporta all'interno della scena.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_BoundaryVisualizationProfile.png" width="650px" alt="Boundry Visualization Settings" style="display:block;">

---
<a name="teleportation"></a>

## <a name="teleportation-system-selection"></a>Selezione del sistema di teletrasporto

L'Project realtà mista offre un sistema di teletrasporto completo per la gestione degli eventi di teletrasporto nel progetto selezionato per impostazione predefinita.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_TeleportationSystemSelection.png" width="650px" alt="Teleport System settings" style="display:block;">

---
<a name="spatialawareness"></a>

## <a name="spatial-awareness-settings"></a>Impostazioni di consapevolezza spaziale

L'Project realtà mista offre un sistema di consapevolezza spaziale ricompilato per l'uso dei sistemi di scansione spaziale nel progetto selezionato per impostazione predefinita.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessSystemSelection.png" width="650px" alt="Spatial Awareness settings 1" style="display:block;">

La configurazione di riconoscimento Toolkit realtà mista consente di personalizzare la modalità di avvio del sistema, sia che sia automaticamente all'avvio dell'applicazione o in un secondo momento a livello di codice, nonché di impostare gli extent per il campo di visualizzazione.

Consente anche di configurare le impostazioni di mesh e superficie, personalizzando ulteriormente il modo in cui il progetto comprende l'ambiente circostante.

Questo è applicabile solo per i dispositivi che possono fornire un ambiente analizzato.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessProfile.png" width="650px" alt="Spatial Awareness settings 2" style="display:block;">

---
<a name="diagnostic"></a>

## <a name="diagnostics-settings"></a>Impostazioni di diagnostica

Una funzionalità facoltativa ma estremamente utile di MRTK è la funzionalità di diagnostica del plug-in.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsSystemSelection.png" width="650px" alt="Diagnostics settings" style="display:block;">

Il profilo di diagnostica offre diversi sistemi semplici da monitorare durante l'esecuzione del progetto, tra cui un pratico interruttore On/Off per abilitare/disabilitare il pannello di visualizzazione nella scena.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsProfile.png" width="650px" alt="Diagnostics settings System settings 2" style="display:block;">

---
<a name="scenesystem"></a>

## <a name="scene-system-settings"></a>Impostazioni di sistema della scena

MrTK fornisce questo servizio facoltativo che consente di gestire il caricamento/scaricamento di scene additive complesse. Per decidere se il sistema di scena è adatto per il progetto, leggere la Guida al Attività iniziali [scene.](../features/scene-system/scene-system-getting-started.md)

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SceneSystemProfile.png" width="650px" alt="Scene System settings 1" style="display:block;">

---
<a name="services"></a>

## <a name="additional-services-settings"></a>Impostazioni aggiuntive dei servizi

Una delle aree più avanzate di Mixed Reality [](https://en.wikipedia.org/wiki/Service_locator_pattern) Toolkit è l'implementazione del modello di localizzatore di servizi che consente la registrazione di qualsiasi "servizio" con il framework. In questo modo il framework può essere esteso con facilità con nuove funzionalità/sistemi, ma consente anche ai progetti di sfruttare queste funzionalità per registrare i propri componenti di runtime.

Qualsiasi servizio registrato ottiene comunque il massimo vantaggio di tutti gli eventi unity, senza il sovraccarico e il costo dell'implementazione di modelli singleton MonoBehaviour o clunky. Ciò consente componenti C# puri senza sovraccarico della scena per l'esecuzione di processi in primo piano e in background, ad esempio sistemi di generazione, logica di gioco di runtime o praticamente qualsiasi altra operazione.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_RegisteredServiceProvidersProfile.png" width="650px" alt="additional System settings" style="display:block;">

---
<a name="inputactions"></a>

## <a name="input-actions-settings"></a>Impostazioni delle azioni di input

Le azioni di input consentono di astrarre eventuali interazioni fisiche e input da un progetto di runtime. Tutto l'input fisico (da controller/ mani/ mouse / e così via) viene convertito in un'azione di input logica da usare nel progetto di runtime. In questo modo, indipendentemente dalla posizione di origine dell'input, il progetto implementa semplicemente queste azioni come "Cose da fare" o "Interagisci con" nelle scene.

Per creare una nuova azione di input, è sufficiente fare clic sul pulsante "Aggiungi una nuova azione" e immettere un nome di testo descrittivo per ciò che rappresenta. È quindi necessario selezionare solo un asse (il tipo di dati) a cui l'azione deve trasmettere o, nel caso dei controller fisici, il tipo di input fisico a cui può essere collegata, ad esempio:

| Vincolo dell'asse | Tipo di dati | Descrizione | Uso di esempio |
| :--- | :--- | :--- | :--- |
| Nessuno | Nessun dato | Usato per un'azione o un evento vuoto | Trigger di evento |
| Non elaborato (riservato) | object | Riservate per utilizzo futuro | N/D |
| Digitale | bool | Dati booleani di tipo on o off | Pulsante controller |
| Asse singolo | float | Un singolo valore di dati di precisione | Input con intervallo, ad esempio un trigger |
| Doppio asse | Vector2 | Data di tipo float doppio per più assi | Un Dpad o una levetta |
| Posizione di tre dof | Vector3 | Dati di tipo posizionale da con 3 assi float | Controller solo stile di posizione 3D |
| Rotazione di tre dof | Quaternion | Input solo rotazionale con 4 assi float | Un controller di stile a tre gradi, ad esempio un controller Oculus Go |
| Sei Dof | Pose di realtà mista (Vector3, Quaternion) | Input di posizione e stile di rotazione con componenti Vector3 e Quaternion | Un controller di movimento o un puntatore |

Gli eventi che utilizzano azioni di input non sono limitati ai controller fisici e possono comunque essere utilizzati all'interno del progetto per fare in modo che gli effetti di runtime generino nuove azioni.

> [!NOTE]
> Le azioni di input sono uno dei pochi componenti non modificabili in fase di esecuzione, ma sono solo una configurazione in fase di progettazione. Questo profilo non deve essere scambiato mentre il progetto è in esecuzione a causa della dipendenza del framework (e dei progetti) dall'ID generato per ogni azione.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionsProfile.png" width="650px" alt="Configuration Profile" style="display:block;">

---
<a name="inputactionrules"></a>

## <a name="input-actions-rules"></a>Regole delle azioni di input

Le regole di azione di input consentono di convertire automaticamente un evento generato per un'azione di input in azioni diverse in base al valore dei dati. Questi vengono gestiti senza problemi all'interno del framework e non comportano costi per le prestazioni.

Ad esempio, convertendo il singolo evento di input del doppio asse da un DPad in alle 4 azioni "Dpad Up" /"DPad Down" /"Dpad Left" /"Dpad Right" corrispondenti (come illustrato nell'immagine seguente).

Questa operazione può essere eseguita anche nel codice. Tuttavia, poiché si tratta di un modello molto comune, il framework fornisce un meccanismo per eseguire questa operazione "predefinita"

Le regole dell'azione di input possono essere configurate per qualsiasi asse di input disponibile. Tuttavia, le azioni di input da un tipo di asse possono essere convertite in un'altra azione di input dello stesso tipo di asse. È possibile eseguire il mapping di un'azione del doppio asse a un'altra azione del doppio asse, ma non a un'azione digitale o nessuna.

![Profilo delle regole di azione di input](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionRulesProfile.png)

---
<a name="pointer"></a>

## <a name="pointer-configuration"></a>Configurazione del puntatore

I puntatori vengono usati per guidare l'interattività nella scena da qualsiasi dispositivo di input, fornendo sia una direzione che un hit test con qualsiasi oggetto in una scena (che ha un collisore collegato o è un componente dell'interfaccia utente). Per impostazione predefinita, i puntatori vengono configurati automaticamente per controller, visori (sguardo fisso/messa a fuoco) e input tramite mouse/tocco.

I puntatori possono anche essere visualizzati all'interno della scena attiva usando uno dei numerosi componenti di linea forniti dal Toolkit di realtà mista o uno dei propri se implementano l'interfaccia MRTK IMixedRealityPointer.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputPointerProfile.png" width="650px" alt="Input Pointer Profile" style="display:block;">

- Extent di puntamento: determina l'extent di puntamento globale per tutti i puntatori, incluso lo sguardo fisso.
- Maschere di livello Raycast di puntamento: determina su quali livelli verranno raggiati i puntatori.
- Debug di raggi di puntamento di disegno: un helper di debug per la visualizzazione dei raggi usati per il raycasting.
- Debug dei colori dei raggi di disegno: set di colori da usare per la visualizzazione.
- Prefab cursore sguardo fisso: semplifica la specifica di un cursore globale per qualsiasi scena.

È presente un pulsante helper aggiuntivo per passare rapidamente al provider gaze per eseguire l'override di alcuni valori specifici per Gaze, se necessario.

---
<a name="gestures"></a>

## <a name="gestures-configuration"></a>Configurazione dei movimenti

I movimenti sono un'implementazione specifica del sistema che consente di assegnare azioni di input ai vari metodi di input "Gesture" forniti da vari SDK (ad esempio HoloLens).

> [!NOTE]
> L'implementazione corrente di Gestures è solo per il HoloLens e verrà migliorata per altri sistemi in quanto verranno aggiunti al Toolkit in futuro (nessuna data).

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_GesturesProfile.png" width="650px" alt="Gesture configuration" style="display:block;">

---
<a name="speech"></a>

## <a name="speech-commands"></a>Comandi vocali

Analogamente ai movimenti, alcune piattaforme di runtime offrono anche funzionalità intelligenti di Riconoscimento vocale con la possibilità di generare comandi che possono essere ricevuti da un progetto Unity. Questo profilo di configurazione consente di configurare quanto segue:

1. Impostazioni Impostazioni: "Comportamento di avvio" impostato su Avvio automatico o Avvio manuale determina se inizializzare KeywordRecognizer all'avvio del sistema di input o lasciare che il progetto decida quando inizializzare KeywordRecognizer. Il "livello di attendibilità del riconoscimento" viene usato per inizializzare [l'API KeywordRecognizer di](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html) Unity
2. Comandi vocali: registra le "parole" e le converte in azioni di input che possono essere ricevute dal progetto. Possono anche essere collegati alle azioni della tastiera, se necessario.

> [!IMPORTANT]
> Il sistema attualmente supporta il riconoscimento vocale solo quando viene eseguito su piattaforme Windows 10, ad esempio HoloLens e Windows 10 Desktop e verrà migliorato per altri sistemi in quanto verranno aggiunti a MRTK in futuro (nessuna data).

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpeechCommandsProfile.png" width="650px" alt="Configuration Profile screens" style="display:block;">

---
<a name="mapping"></a>

## <a name="controller-mapping-configuration"></a>Configurazione del mapping dei controller

Una delle schermate di configurazione principali per Toolkit realtà mista è la possibilità di configurare ed eseguire il mapping dei vari tipi di controller che possono essere utilizzati dal progetto.

La schermata di configurazione seguente consente di configurare uno dei controller attualmente riconosciuti dal toolkit.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerMappingProfile.png" width="650px" alt="Controller Mapping" style="display:block;">

MrTK fornisce una configurazione predefinita per i controller/sistemi seguenti:

- Mouse (incluso il supporto del mouse spaziale 3D)
- Touch screen
- Controller Xbox
- Windows Mixed Reality controller
- HoloLens Gesti
- CONTROLLER WAND DI VIVE IN STATO DI INSODATI
- Controller Oculus Touch
- Controller remoto Oculus
- Dispositivi OpenVR generici (solo utenti esperti)

Facendo clic sull'immagine per uno dei sistemi controller predefiniti è possibile configurare una singola azione di input per tutti gli input corrispondenti, ad esempio, vedere la schermata di configurazione del controller Oculus Touch riportata di seguito:

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_WindowsMixedRealityControllerConfigScreen.png" width="650px" alt="Controller config screen" style="display:block;">

È disponibile anche una schermata avanzata per la configurazione di altri controller di input OpenVR o Unity non identificati in precedenza.

---
<a name="visualization"></a>

## <a name="controller-visualization-settings"></a>Impostazioni di visualizzazione del controller

Oltre al mapping del controller, viene fornito un profilo di configurazione separato per personalizzare il modo in cui i controller vengono presentati all'interno delle scene.

Questo può essere configurato in un "Globale" (tutte le istanze di un controller per una mano specifica) o specifico per un singolo tipo di controller/mano.

MrTK supporta anche modelli di controller SDK nativi per Windows Mixed Reality e OpenVR. Vengono caricati come GameObject nella scena e posizionati usando il monitoraggio del controller della piattaforma.

Se la rappresentazione del controller nella scena deve essere compensata dalla posizione del controller fisico, è sufficiente impostare tale offset rispetto al prefab del modello controller (ad esempio, impostando la posizione di trasformazione del prefab controller con una posizione di offset).

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerVisualizationProfile.png" width="650px" alt="Visualization profile" style="display:block;">

<a name="editor-utilities"></a>

## <a name="editor-utilities"></a>Utilità dell'editor

Le utilità seguenti funzionano solo nell'editor e sono utili per migliorare la produttività dello sviluppo.

![Utilità di configurazione dell'editor MRTK](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_EditorConfiguration.png)

### <a name="service-inspectors"></a>Controlli dei servizi

I controlli dei servizi sono una funzionalità solo editor che genera oggetti nella scena che rappresentano i servizi attivi. Selezionando questi oggetti vengono visualizzati i controlli che offrono collegamenti alla documentazione, controllano le visualizzazioni dell'editor e informazioni dettagliate sullo stato del servizio.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ServiceInspectors.PNG" width="350px" alt="Service Inspectors" style="display:block;">

È possibile abilitare i controlli dei servizi selezionando *Usa controlli servizio* in Editor *Impostazioni* nel profilo di configurazione.

### <a name="depth-buffer-renderer"></a>Renderer del buffer di profondità

La condivisione del buffer di profondità con alcune piattaforme di realtà mista può migliorare [la stabilizzazione dell'ologramma.](../performance/hologram-stabilization.md) Ad esempio, la piattaforma Windows Mixed Reality può modificare la scena sottoposta a rendering per pixel in modo da rendere conto dei piccoli movimenti della testa durante il tempo necessario per il rendering di un frame. Tuttavia, queste tecniche richiedono buffer di profondità con dati accurati per sapere dove e quanto è distante la geometria dall'utente.

Per assicurarsi che una scena eserciti il rendering di tutti i dati necessari nel buffer di profondità, gli sviluppatori possono attivare o disattivare la funzionalità *Buffer* di profondità di rendering in *Editor Impostazioni* nel profilo di configurazione. Verrà utilizzato il buffer di profondità corrente e ne verrà eseguito il rendering come colore per la visualizzazione della scena applicando un effetto di post-elaborazione, [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer) , alla fotocamera principale.

![Utilità buffer di profondità di rendering Il cilindro blu nella scena ha un materiale ](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
 <sup>con ZWrite disattivato in modo</sup> che non siano scritti dati di profondità

## <a name="changing-profiles-at-runtime"></a>Modifica dei profili in fase di esecuzione

È possibile aggiornare i profili in fase di esecuzione e in genere esistono due scenari e orari diversi in cui ciò risulta utile:

1. Pre-opzione del profilo di inizializzazione **MRTK:** all'avvio, prima dell'inizializzazione di MRTK e del profilo diventa attivo, sostituendo il profilo non ancora in uso per abilitare o disabilitare funzionalità diverse in base alle funzionalità del dispositivo. Ad esempio, se l'esperienza è in esecuzione nella realtà virtuale che non dispone di hardware di mapping spaziale, probabilmente non ha senso che il componente di mapping spaziale sia abilitato.
1. **Opzione profilo attivo:** dopo l'avvio, dopo l'inizializzazione di MRTK e l'attivazione di un profilo, lo scambio del profilo attualmente in uso per modificare il comportamento di determinate funzionalità. Ad esempio, potrebbe essere presente un'esperienza secondaria specifica nell'applicazione che vuole che i puntatori a mano lontano siano completamente rimossi.

### <a name="pre-mrtk-initialization-profile-switch"></a>Opzione del profilo di inizializzazione MRTK precedente

Questa operazione può essere eseguita collegando un monobehaviour (esempio seguente) che viene eseguito prima dell'inizializzazione di MRTK (ad esempio, Awake()). Si noti che lo script (ad esempio, la chiamata a ) deve essere eseguito prima dello script, operazione che può essere ottenuta impostando le `SetProfileBeforeInitialization` `MixedRealityToolkit` impostazioni [dell'ordine di esecuzione dello script](https://docs.unity3d.com/Manual/class-MonoManager.html).

```csharp
using Microsoft.MixedReality.Toolkit;
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
public class PreInitProfileSwapper : MonoBehaviour
{

    [SerializeField]
    private MixedRealityToolkitConfigurationProfile profileToUse = null;

    private void Awake()
    {
        // Here you could choose any arbitrary MixedRealityToolkitConfigurationProfile (for example, you could
        // add some platform checking code here to determine which profile to load).
        MixedRealityToolkit.SetProfileBeforeInitialization(profileToUse);
    }
}
```

Invece di "profileToUse", è possibile avere un set arbitrario di profili che si applicano a piattaforme specifiche (ad esempio, uno per HoloLens 1, uno per la realtà virtuale, uno per HoloLens 2 e così via). È possibile usare vari altri indicatori (ad esempio , o se la fotocamera è opaca/trasparente) per determinare il profilo https://docs.unity3d.com/ScriptReference/SystemInfo.html da caricare.

### <a name="active-profile-switch"></a>Opzione del profilo attivo

A tale scopo, impostare la `MixedRealityToolkit.Instance.ActiveProfile` proprietà su un nuovo profilo sostituendo il profilo attivo.

```csharp
MixedRealityToolkit.Instance.ActiveProfile = profileToUse;
```

Si noti che quando si imposta durante il runtime, l'eliminazione dei servizi attualmente in esecuzione verrà eseguita dopo l'ultimo LateUpdate() di tutti i servizi e la creazione di istanze e l'inizializzazione dei servizi associati al nuovo profilo verranno eseguite prima del primo Update() di tutti i `ActiveProfile` servizi.

Durante questo processo può verificarsi un'esitazione notevole dell'applicazione. Inoltre, qualsiasi script con priorità più alta rispetto allo `MixedRealityToolkit` script può immettere il relativo aggiornamento prima che il nuovo profilo sia configurato correttamente. Per [altre informazioni sulla priorità degli script,](https://docs.unity3d.com/Manual/class-MonoManager.html) vedere Impostazioni dell'ordine di esecuzione degli script.

Nel processo di cambio del profilo la fotocamera dell'interfaccia utente esistente rimarrà invariata, assicurando che i componenti dell'interfaccia utente di Unity che richiedono l'area di disegno funzionino ancora dopo il passaggio.

## <a name="see-also"></a>Vedi anche

- [Stabilizzazione dell'ologramma](../performance/hologram-stabilization.md)
