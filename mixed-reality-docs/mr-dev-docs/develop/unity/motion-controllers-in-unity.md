---
title: Controller di movimento in Unity
description: Informazioni su come intervenire sullo sguardo in Unity con l'input del controller di movimento usando XR e API comuni per pulsanti e assi.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: controller di movimento, unity, input, visore per realtà mista, visore windows mixed reality, visore per realtà virtuale, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: d8f9ce292c0ab1cfa89faf58f0e5b90322192b35
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394515"
---
# <a name="motion-controllers-in-unity"></a>Controller di movimento in Unity

Esistono due modi chiave per intervenire sullo [](../../design/gaze-and-commit.md#composite-gestures) sguardo [in Unity,](gaze-in-unity.md)movimenti della mano e controller del movimento [in](../../design/motion-controllers.md) HoloLens e immersive HMD. È possibile accedere ai dati per entrambe le origini di input spaziale tramite le stesse API in Unity.

Unity offre due modi principali per accedere ai dati di input spaziali per Windows Mixed Reality. Le API *Comuni Input.GetButton/Input.GetAxis* funzionano in più SDK XR unity, mentre l'API *InteractionManager/GestureRecognizer* specifica per Windows Mixed Reality espone il set completo di dati di input spaziali.

## <a name="unity-xr-input-apis"></a>API di input XR di Unity

Per i nuovi progetti, è consigliabile usare le nuove API di input XR dall'inizio. 

Altre informazioni sulle [API XR sono](https://docs.unity3d.com/Manual/xr_input.html)disponibili qui.

## <a name="unity-buttonaxis-mapping-table"></a>Tabella di mapping di pulsanti/assi unity

Gestione input di Unity per Windows Mixed Reality di movimento supporta gli ID pulsante e asse elencati di seguito tramite le API *Input.GetButton/GetAxis.* La colonna "Windows MR-specific" fa riferimento alle proprietà disponibili al di fuori del *tipo InteractionSourceState.* Ognuna di queste API è descritta in dettaglio nelle sezioni seguenti.

I mapping degli ID pulsante/asse per Windows Mixed Reality in genere corrispondono al pulsante Oculus/ID asse.

I mapping degli ID pulsante/asse per Windows Mixed Reality diversi dai mapping di OpenVR in due modi:
1. Il mapping usa ID touchpad distinti dalla levetta personale, per supportare i controller sia con le leve che con i touchpad.
2. Il mapping evita l'overload degli ID dei pulsanti A e X per i pulsanti di menu per lasciarli disponibili per i pulsanti ABXY fisici.

<table>
<tr>
<th rowspan="2">Input </th><th colspan="2"><a href="motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">API Unity comuni</a><br />(Input.GetButton/GetAxis) </th><th rowspan="2"><a href="motion-controllers-in-unity.md#windows-specific-apis-xrwsainput">API di input specifica di MR di Windows</a><br />(XR. Wsa. Input)</th>
</tr><tr>
<th> Mano sinistra </th><th> Mano destra</th>
</tr><tr>
<td> Selezionare il trigger premuto </td><td> Asse 9 = 1,0 </td><td> Asse 10 = 1,0 </td><td> selectPressed</td>
</tr><tr>
<td> Selezionare il valore analogico del trigger </td><td> Asse 9 </td><td> Asse 10 </td><td> selectPressedAmount</td>
</tr><tr>
<td> Selezionare il trigger parzialmente premuto </td><td> Pulsante 14 <i>(gamepad compat)</i> </td><td> Pulsante 15 <i>(gamepad compat)</i> </td><td> selectPressedAmount &gt; 0.0</td>
</tr><tr>
<td> Pulsante di menu premuto </td><td> Pulsante 6* </td><td> Pulsante 7* </td><td> menuPressed</td>
</tr><tr>
<td> Pulsante di controllo premuto </td><td> Asse 11 = 1,0 (nessun valore analogo)<br />Pulsante 4 <i>(gamepad compat)</i> </td><td> Asse 12 = 1,0 (nessun valore analogo)<br />Pulsante 5 <i>(gamepad compat)</i> </td><td> Afferrato</td>
</tr><tr>
<td> Levetta X <i>(a sinistra: -1.0, a destra: 1.0)</i> </td><td> Asse 1 </td><td> Asse 4 </td><td> thumbstickPosition.x</td>
</tr><tr>
<td> Thumbstick Y <i>(top: -1.0, bottom: 1.0)</i> </td><td> Asse 2 </td><td> Asse 5 </td><td> thumbstickPosition.y</td>
</tr><tr>
<td> Levetta premuta </td><td> Pulsante 8 </td><td> Pulsante 9 </td><td> thumbstickPressed</td>
</tr><tr>
<td> Touchpad X <i>(a sinistra: -1.0, a destra: 1.0)</i> </td><td> Asse 17* </td><td> Asse 19* </td><td> touchpadPosition.x</td>
</tr><tr>
<td> Touchpad Y <i>(in alto: -1.0, in basso: 1.0)</i> </td><td> Asse 18* </td><td> Asse 20* </td><td> touchpadPosition.y</td>
</tr><tr>
<td> Touchpad toccato </td><td> Pulsante 18* </td><td> Pulsante 19* </td><td> touchpadTouched</td>
</tr><tr>
<td> Touchpad premuto </td><td> Pulsante 16* </td><td> Pulsante 17* </td><td> touchpadPressed</td>
</tr><tr>
<td> 6Sottosto aderenza o posizione del puntatore </td><td colspan="2"> <i>Solo</i> posizione di presa: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR. InputTracking.GetLocalPosition</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">Xr. InputTracking.GetLocalRotation</a></td><td> Passare <i>Grip</i> o <i>Pointer</i> come argomento: sourceState.sourcePose.TryGetPosition<br />sourceState.sourcePose.TryGetRotation<br /></td>
</tr><tr>
<td> Stato di rilevamento </td><td colspan="2"> <i>Accuratezza della posizione e rischio di perdita di origine disponibili solo tramite l'API specifica di MR</i> </td><td> <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></td>
</tr>
</table>

>[!NOTE]
>Questi ID pulsante/asse sono diversi dagli ID usati da Unity per OpenVR a causa di collisioni nei mapping usati da gamepad, Oculus Touch e OpenVR.

<!-- ### Using HP Reverb G2 controllers

If you're using the HP Reverb G2 controllers, refer to the table below for button and axis IDs.

<table>
<tr>
<th rowspan="2"><a href="https://docs.unity3d.com/ScriptReference/XR.CommonUsages.html">Input </th><th colspan="2">Common Unity APIs</a><br />(Input.GetButton/GetAxis) </th><th rowspan="2">HP Reverb G2 Input API</a></th>
</tr><tr>
<th> Left hand </th><th> Right hand</th>
</tr><tr>
<td> Primary2DAxis </td><td> Axis 1 (X) / Axis 2 (Y) </td><td> Axis 4 (X) / Axis 5(Y) </td><td> Thumbstick</td>
</tr><tr>
<td> Trigger pressed </td><td> Axis 9 </td><td> Axis 10 </td><td> Index trigger</td>
</tr><tr>
<td> Grip </td><td> Axis 11d </td><td> Axis 12 </td><td> Grip trigger</td>
</tr><tr>
<td> PrimaryButton pressed </td><td> Button 2 </td><td> Button 0 </td><td> Menu button pressed</td>
</tr><tr>
<td> SecondaryButton pressed </td><td> Button 3 </td><td> Button 1 </td><td> A/X button</td>
</tr><tr>
<td> GripButton </td><td> Button 4 </td><td> Button 5 </td><td> Grip trigger</td>
</tr><tr>
<td> TriggerButton </td><td> Button 14 </td><td> Button 15 </td><td> Index trigger</td>
</tr><tr>
</tr>
</table> -->

### <a name="openxr"></a>OpenXR

Per informazioni di base sulle interazioni di realtà mista in Unity, vedere il Manuale [di Unity per l'input XR di Unity.](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html) Questa documentazione di Unity illustra i mapping da input specifici del controller a input **più** generalizzabili, in che modo gli input XR disponibili possono essere identificati e categorizzati, come leggere i dati da questi input e altro ancora.

Il plug-in OpenXR di realtà mista offre profili di interazione di input aggiuntivi, mappati a **InputFeatureUsage** standard, come descritto di seguito:

| InputFeatureUsage | Controller HP Reverb G2 (OpenXR) | Mano holoLens (OpenXR) |
| ---- | ---- | ---- |
| primary2DAxis | Joystick | |
| primary2DAxisClick | Joystick - Fare clic su | |
| trigger | Trigger  | |
| Presa | Presa | Tocco o compressione dell'aria |
| primaryButton | [X/A] - Premere | Simulazione del tocco |
| secondaryButton | [Y/B] - Premere | |
| controllo gripButton | Grip - Premere | |
| triggerButton | Trigger - Premere | |
| menuButton | Menu | |

## <a name="grip-pose-vs-pointing-pose"></a>Posizione di aderenza rispetto alla posizione di puntamento

Windows Mixed Reality supporta i controller di movimento in un'ampia gamma di fattori di forma. La progettazione di ogni controller differisce nella relazione tra la posizione della mano dell'utente e la direzione naturale "avanti" che le app devono usare per puntare durante il rendering del controller.

Per rappresentare meglio questi controller, è possibile analizzare due tipi di  pose per ogni origine di interazione, la posizione del grip e il **puntatore.** Entrambe le coordinate di posizione e di posizione del puntatore del puntatore sono espresse da tutte le API unity nelle coordinate globali del mondo unity.

### <a name="grip-pose"></a>Posizione del grip

La **posizione del grip** rappresenta la posizione del palmo degli utenti, rilevata da un HoloLens o che tiene in mano un controller di movimento.

Nei visori immersivi, la posizione del grip è più adatta per eseguire il rendering della mano **dell'utente** o di un oggetto in mano **dell'utente.** La posizione del grip viene usata anche quando si visualizza un controller di movimento. Il **modello di rendering fornito** da Windows per un controller di movimento usa la posizione di presa come origine e centro di rotazione.

La posizione del grip è definita in modo specifico come segue:
* Posizione **del grip:** centroide del palmo quando si tiene il controller naturalmente, regolato a sinistra o a destra per centrare la posizione all'interno del grip. Nel controller Windows Mixed Reality movimento, questa posizione è in genere allineata al pulsante Afferra.
* Asse destro dell'orientamento del grip: quando si apre completamente la mano per formare una posizione a 5 dita piana, il raggio normale al palmo (in avanti dal palmo sinistro, **all'indietro** dal palmo destro)
* Asse avanti **dell'orientamento** del grip: quando si chiude parzialmente la mano (come se si tiene il controller), il raggio che punta in avanti attraverso il canale formato dalle dita non del pollice.
* Asse **su dell'orientamento del** grip: asse Su implicito dalle definizioni Right e Forward.

È possibile accedere alla posizione del grip tramite l'API di input tra fornitori di Unity *[(XR). InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation*) o tramite l'API specifica di Windows MR (*sourceState.sourcePose.TryGetPosition/Rotation,* che richiede dati di posizione per il **nodo Grip).**

### <a name="pointer-pose"></a>Posizione del puntatore

La **posizione del puntatore** rappresenta la punta del controller che punta in avanti.

La posizione del puntatore fornita dal sistema è più adatta per eseguire il raycast quando si esegue il **rendering del modello controller stesso.** Se si esegue il rendering di un altro oggetto virtuale al posto del controller, ad esempio una mitragliatrice virtuale, è consigliabile puntare con un raggio più naturale per tale oggetto virtuale, ad esempio un raggio che viaggia lungo la canna del modello di mitra definito dall'app. Poiché gli utenti possono visualizzare l'oggetto virtuale e non il controller fisico, puntare all'oggetto virtuale sarà probabilmente più naturale per gli utenti che usano l'app.

Attualmente, la posizione del puntatore è disponibile in Unity solo tramite l'API specifica di Windows MR, *sourceState.sourcePose.TryGetPosition/Rotation,* passando *InteractionSourceNode.Pointer* come argomento.

### <a name="openxr"></a>OpenXR 

È possibile accedere a due set di pose tramite interazioni di input OpenXR:

* Il grip si pone per il rendering degli oggetti nella mano
* L'obiettivo è puntare al mondo.

Altre informazioni su questa progettazione e sulle differenze tra le due posizioni sono disponibili nella specifica [OpenXR - Sottopercorso di input](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).

Le posizioni fornite da InputFeatureUsages **DevicePosition,** **DeviceRotation,** **DeviceVelocity** e **DeviceAngularVelocity** rappresentano tutte la posizione del grip OpenXR.  InputFeatureUsages correlati alle posizioni di aderenza sono definiti in [CommonUsages di](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)Unity.

Le posizioni fornite da InputFeatureUsages **PointerPosition,** **PointerRotation,** **PointerVelocity** e **PointerAngularVelocity** rappresentano tutte la posizione dell'obiettivo OpenXR.  Questi InputFeatureUsages non sono definiti in alcun file C# incluso, quindi è necessario definire inputFeatureUsages come indicato di seguito:

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

## <a name="haptics"></a>Aptics

Per informazioni sull'uso dell'aptica nel sistema XR Input di Unity, la documentazione è disponibile nel manuale [Unity per Unity XR Input - Haptics.](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics)

## <a name="controller-tracking-state"></a>Stato di rilevamento del controller

Come i visori, il controller Windows Mixed Reality movimento non richiede la configurazione di sensori di rilevamento esterni. I controller vengono invece monitorati dai sensori nel visore stesso.

Se l'utente sposta i controller fuori dal campo di visualizzazione del visore, Windows continua a dedurre le posizioni del controller nella maggior parte dei casi. Quando il controller ha perso il rilevamento visivo per un tempo sufficiente, le posizioni del controller scenderanno a posizioni di accuratezza approssimativa.

A questo punto, il sistema bloczzerà il controller all'utente, tenendo traccia della posizione dell'utente mentre si sposta, pur esponendo il vero orientamento del controller usando i sensori di orientamento interni. Molte app che usano controller per puntare e attivare gli elementi dell'interfaccia utente possono funzionare normalmente con accuratezza approssimativa senza che l'utente se ne sia abiliti.

<!-- The best way to get a feel for this is to try it yourself. Check out this video with examples of immersive content that works with motion controllers across various tracking states:

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g] -->

### <a name="reasoning-about-tracking-state-explicitly"></a>Ragionamento sul rilevamento dello stato in modo esplicito

Le app che vogliono trattare le posizioni in modo diverso in base allo stato di rilevamento possono andare oltre ed esaminare le proprietà sullo stato del controller, ad esempio *SourceLossRisk* e *PositionAccuracy:*

<table>
<tr>
<th> Stato di rilevamento </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td> <b>Accuratezza elevata</b> </td><td style="background-color: green; color: white"> &lt; 1.0 </td><td style="background-color: green; color: white"> Alto </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Accuratezza elevata (a rischio di perdita)</b> </td><td style="background-color: orange"> == 1,0 </td><td style="background-color: green; color: white"> Alto </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Accuratezza approssimativa</b> </td><td style="background-color: orange"> == 1,0 </td><td style="background-color: orange"> Con approssimazione </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Nessuna posizione</b> </td><td style="background-color: orange"> == 1,0 </td><td style="background-color: orange"> Con approssimazione </td><td style="background-color: orange"> false</td>
</tr>
</table>

Questi stati di rilevamento del controller di movimento sono definiti come segue:
* **Accuratezza elevata:** Mentre il controller di movimento si trova all'interno del campo visivo del visore, in genere fornirà posizioni di accuratezza elevata, in base al rilevamento visivo. Un controller in movimento che lascia momentaneamente il campo di visualizzazione o viene momentaneamente nascosto dai sensori del visore (ad esempio, dall'altra mano dell'utente) continuerà a restituire pose ad alta accuratezza per un breve periodo di tempo, in base al rilevamento inerziale del controller stesso.
* **Accuratezza elevata (a rischio di perdita):** Quando l'utente sposta il controller di movimento oltre il bordo del campo visivo del visore, il visore non sarà presto in grado di rilevare visivamente la posizione del controller. L'app sa quando il controller ha raggiunto questo limite FOV, verificando che **SourceLossRisk** raggiunga la versione 1.0. A questo punto, l'app può scegliere di sospendere i movimenti del controller che richiedono un flusso costante di pose di alta qualità.
* **Accuratezza approssimativa:** Quando il controller ha perso il rilevamento visivo per un tempo sufficiente, le posizioni del controller scenderanno a posizioni di accuratezza approssimativa. A questo punto, il sistema bloczzerà il controller all'utente, tenendo traccia della posizione dell'utente mentre si sposta, pur esponendo il vero orientamento del controller usando i sensori di orientamento interni. Molte app che usano controller per puntare e attivare gli elementi dell'interfaccia utente possono funzionare normalmente con accuratezza approssimativa senza che l'utente se ne sia abiliti. Le app con requisiti di input più  elevati  possono scegliere di percepire questo calo da Accuratezza elevata a Accuratezza approssimativa controllando la **proprietà PositionAccuracy,** ad esempio per offrire all'utente un hitbox più ampio sulle destinazioni fuori schermo durante questo periodo.
* **Nessuna posizione:** Anche se il controller può operare a un'accuratezza approssimativa per molto tempo, a volte il sistema sa che anche una posizione bloccata dal corpo non è significativa al momento. Ad esempio, un controller che è stato attivato potrebbe non essere mai stato osservato visivamente o un utente può disattivare un controller che viene quindi prelevato da un altro utente. In questi casi, il sistema non fornirà alcuna posizione all'app e *TryGetPosition* restituirà false.

## <a name="common-unity-apis-inputgetbuttongetaxis"></a>API Comuni di Unity (Input.GetButton/GetAxis)

**Spazio dei nomi:** *UnityEngine,* *UnityEngine.XR*<br>
**Tipi**: *Input*, *XR. InputTracking*

Unity attualmente usa le API *Input.GetButton/Input.GetAxis* generali per esporre l'input per [Oculus SDK,](https://docs.unity3d.com/Manual/OculusControllers.html) [OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) e Windows Mixed Reality, inclusi mani e controller di movimento. Se l'app usa queste API per l'input, può supportare facilmente i controller di movimento in più SDK XR, inclusi Windows Mixed Reality.

### <a name="getting-a-logical-buttons-pressed-state"></a>Recupero dello stato premuto di un pulsante logico

Per usare le API di input di Unity generali, in genere si inizierà cablando pulsanti e assi ai nomi logici in [Unity Input Manager,](https://docs.unity3d.com/Manual/ConventionalGameInput.html)associando un ID pulsante o asse a ogni nome. È quindi possibile scrivere codice che faccia riferimento al nome logico del pulsante o dell'asse.

Ad esempio, per eseguire il mapping del pulsante trigger del controller del movimento sinistro all'azione Invia, passare > Modifica impostazioni progetto **> Input in** Unity ed espandere le proprietà della sezione Invia in Assi. Modificare la **proprietà Pulsante positivo** o Alt **Pulsante** positivo in modo da leggere il pulsante con **il joystick 14,** come illustrato di codice seguente:

![InputManager di Unity](images/unity-input-manager.png)<br>
*Unity InputManager*

Lo script può quindi cercare l'azione Submit usando *Input.GetButton:*

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
È possibile aggiungere altri pulsanti logici modificando la **proprietà Size** in **Axes**.

### <a name="getting-a-physical-buttons-pressed-state-directly"></a>Recupero diretto dello stato premuto di un pulsante fisico

È anche possibile accedere ai pulsanti manualmente in base al nome completo, *usando Input.GetKey:*

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a>Ottenere la posizione di una mano o di un controller del movimento

È possibile accedere alla posizione e alla rotazione del controller usando *XR. InputTracking*:

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

> [!NOTE] 
> Il codice precedente rappresenta la posizione del punto di controllo del controller (in cui l'utente tiene il controller), utile per il rendering di un'avaria o di una minaccia nella mano dell'utente o di un modello del controller stesso.
> 
> La relazione tra la posizione del controllo e la posizione dell'indicatore di misura (in cui la punta del controller punta) può variare tra i controller. Al momento, l'accesso alla posizione del puntatore del controller è possibile solo tramite l'API di input specifica di MR, descritta nelle sezioni seguenti.

## <a name="windows-specific-apis-xrwsainput"></a>API specifiche di Windows (XR. Wsa. Input)

> [!CAUTION]
> Se il progetto usa una delle versioni XR. Le API WSA vengono gradualmente sfasati a favore di XR SDK nelle versioni future di Unity. Per i nuovi progetti, è consigliabile usare XR SDK dall'inizio. Altre informazioni sul sistema [di input XR e sulle API sono](https://docs.unity3d.com/Manual/xr_input.html)disponibili qui.

**Spazio dei nomi:** *UnityEngine.XR.WSA.Input*<br>
**Tipi:** *InteractionManager,* *InteractionSourceState,* *InteractionSource,* *InteractionSourceProperties,* *InteractionSourceKind,* *InteractionSourceLocation*

Per ottenere informazioni più dettagliate sull'input manuale Windows Mixed Reality (per HoloLens) e sui controller del movimento, puoi scegliere di usare le API di input spaziale specifiche di Windows nello spazio dei nomi *UnityEngine.XR.WSA.Input.* Ciò consente di accedere a informazioni aggiuntive, ad esempio l'accuratezza della posizione o il tipo di origine, consentendo di distogliere mani e controller.

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a>Polling dello stato delle mani e dei controller del movimento

È possibile eseguire il polling dello stato di questo frame per ogni origine di interazione (mano o controller del movimento) usando *il metodo GetCurrentReading.*

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

Ogni *InteractionSourceState che* ottieni rappresenta un'origine di interazione nel momento corrente. *InteractionSourceState espone* informazioni come:
* Quali [tipi di pressione si](../../design/motion-controllers.md) verificano (Seleziona/Menu/Afferra/Touchpad/Levetta)

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* Altri dati specifici dei controller del movimento, ad esempio le coordinate XY del touchpad e/o della levetta e lo stato toccato

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```

* InteractionSourceKind per sapere se l'origine è una mano o un controller del movimento

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a>Polling per le posizioni di rendering stimate in avanti

* Quando si esegue il polling dei dati di origine dell'interazione da mani e controller, le posizioni che si ottengono sono posizioni previste in avanti per il momento in cui i fotoni di questo fotogramma raggiungeranno gli occhi dell'utente.  Le posizioni stimate in avanti sono più usate per il **rendering** del controller o di un oggetto mantenuto in ogni fotogramma.  Se la destinazione è una determinata pressione o rilascio con il controller, questo sarà più accurato se si usano le API degli eventi cronologici descritte di seguito.

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* È anche possibile ottenere la posizione della testa stimata in avanti per questo fotogramma corrente.  Come per la posizione di origine, questa opzione è utile per il **rendering** di un cursore, anche se la destinazione di una determinata pressione o rilascio sarà più accurata se si usano le API degli eventi cronologici descritte di seguito.

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a>Gestione degli eventi di origine dell'interazione

Per gestire gli eventi di input quando si verificano con i dati cronologici accurati relativi alla posizione, è possibile gestire gli eventi di origine dell'interazione anziché il polling.

Per gestire gli eventi di origine dell'interazione:
* Registrarsi per un evento di input *InteractionManager.* Per ogni tipo di evento di interazione a cui si è interessati, è necessario sottoscriverlo.

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```

* Gestire l'evento . Dopo aver sottoscritto un evento di interazione, si otterrà il callback quando appropriato. *Nell'esempio SourcePressed* questo si verifica dopo che l'origine è stata rilevata e prima che venga rilasciata o persa.

   ```cs
   void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
       var interactionSourceState = args.state;

       // args.state has information about:
          // targeting head ray at the time when the event was triggered
          // whether the source is pressed or not
          // properties like position, velocity, source loss risk
          // source id (which hand id for example) and source kind like hand, voice, controller or other
   }
   ```

### <a name="how-to-stop-handling-an-event"></a>Come interrompere la gestione di un evento

È necessario interrompere la gestione di un evento quando non si è più interessati all'evento o si elimina l'oggetto che ha sottoscritto l'evento. Per interrompere la gestione dell'evento, annullare la sottoscrizione all'evento.

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a>Elenco di eventi di origine dell'interazione

Gli eventi di origine dell'interazione disponibili sono:
* *InteractionSourceDetected* (l'origine diventa attiva)
* *InteractionSourceLost* (diventa inattivo)
* *InteractionSourcePressed* (tocco, pressione di un pulsante o espressione "Seleziona")
* *InteractionSourceReleased* (fine di un tocco, un pulsante rilasciato o la fine dell'espressione "Seleziona")
* *InteractionSourceUpdated* (sposta o modifica in altro modo uno stato)

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a>Eventi per posizioni di destinazione cronologiche che corrispondono in modo più accurato a una stampa o a un rilascio

Le API di polling descritte in precedenza forniscono all'app posizioni previste in avanti.  Anche se queste posizioni stimate sono ottimali per il rendering del controller o di un oggetto portatile virtuale, le posizioni future non sono ottimali per la destinazione, per due motivi chiave:
* Quando l'utente preme un pulsante su un controller, possono essere presenti circa 20 ms di latenza wireless su Bluetooth prima che il sistema riceva la pressione.
* Quindi, se si usa una posizione stimata in avanti, saranno applicati altri 10-20 ms di stima in avanti per raggiungere l'ora in cui i fotoni del fotogramma corrente raggiungeranno gli occhi dell'utente.

Ciò significa che il polling offre una posizione di origine o una posizione della testa di 30-40 ms in avanti da dove la testa e le mani dell'utente erano effettivamente tornati quando si è verificata la pressione o il rilascio.  Per l'input manuale di HoloLens, anche se non è presente alcun ritardo di trasmissione wireless, si verifica un ritardo di elaborazione simile per rilevare la pressione.

Per definire in modo accurato la destinazione in base alla finalità originale dell'utente per una pressione della mano o del controller, devi usare la posizione di origine o la posizione della testa cronologica dell'evento di input *InteractionSourcePressed* o *InteractionSourceReleased.*

È possibile specificare come destinazione una stampa o un rilascio con dati cronologici sulla posizione dalla testa dell'utente o dal relativo controller:
* La posizione della testa nel momento in cui si è verificato  un movimento o una pressione del controller, che può essere usata per la destinazione per determinare ciò che l'utente stava [guardando:](../../design/gaze-and-commit.md)

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args) {
       var interactionSourceState = args.state;
       var headPose = interactionSourceState.headPose;
       RaycastHit raycastHit;
       if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
           var targetObject = raycastHit.collider.gameObject;
           // ...
       }
   }
   ```

* Posizione di origine nel momento in cui si è verificata  la pressione di un controller del movimento, che può essere usata per la destinazione per determinare a cosa puntava il controller.  Questo sarà lo stato del controller che ha riscontrato la pressione.  Se si esegue il rendering del controller stesso, è possibile richiedere la posizione dell'indicatore di misura anziché la posizione del punto di controllo, per afferrare il raggio di destinazione da ciò che l'utente considererà la punta naturale del controller sottoposto a rendering:

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args)
   {
       var interactionSourceState = args.state;
       var sourcePose = interactionSourceState.sourcePose;
       Vector3 sourceGripPosition;
       Quaternion sourceGripRotation;
       if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Pointer)) &&
           (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Pointer))) {
           RaycastHit raycastHit;
           if (Physics.Raycast(sourceGripPosition, sourceGripRotation * Vector3.forward, out raycastHit, 10)) {
               var targetObject = raycastHit.collider.gameObject;
               // ...
           }
       }
   }
   ```

### <a name="event-handlers-example"></a>Esempio di gestori eventi

```cs
using UnityEngine.XR.WSA.Input;

void Start()
{
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased += InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
}

void OnDestroy()
{
    InteractionManager.InteractionSourceDetected -= InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost -= InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased -= InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;
}

void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
{
    // Source was detected
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceLost(InteractionSourceLostEventArgs state)
{
    // Source was lost. This will be after a SourceDetected event and no other events for this
    // source id will occur until it is Detected again
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs state)
{
    // Source was pressed. This will be after the source was detected and before it is
    // released or lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceReleased(InteractionSourceReleasedEventArgs state)
{
    // Source was released. The source would have been detected and pressed before this point.
    // This event will not fire if the source is lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs state)
{
    // Source was updated. The source would have been detected before this point
    // args.state has the current state of the source including id, position, kind, etc.
}
```

## <a name="motion-controllers-in-mrtk"></a>Controller del movimento in MRTK

È possibile accedere al [movimento e al controller del movimento](/windows/mixed-reality/mrtk-unity/features/input/controllers) da Gestione input.

## <a name="follow-along-with-tutorials"></a>Seguire le esercitazioni

Esercitazioni dettagliate, con esempi di personalizzazione più dettagliati, sono disponibili in Mixed Reality Academy:

- [Input MR 211: Movimento](tutorials/holograms-211.md)
- [Input MR 213: Controller del movimento](../../deprecated/mixed-reality-213.md)

[![Input MR 213 - Controller del movimento](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)<br>
*Input MR 213 - Controller del movimento*

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si sta seguendo il percorso di sviluppo di Unity che è stato strutturato, si stanno esplorando i blocchi predefiniti principali di MRTK. Da qui è possibile passare al blocco predefinito successivo:

> [!div class="nextstepaction"]
> [Tracciamento della mano e oculare](./hand-eye-in-unity.md)

In alternativa, passare alle API e funzionalità della piattaforma di realtà mista:

> [!div class="nextstepaction"]
> [Esperienze condivise](shared-experiences-in-unity.md)

È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#2-core-building-blocks) in qualsiasi momento.

## <a name="see-also"></a>Vedere anche

* [Puntamento con la testa e commit](../../design/gaze-and-commit.md)
* [Controller del movimento](../../design/motion-controllers.md)