---
title: Funzionalità supportate dal plug-in OpenXR in Unity
description: Scoprire le funzionalità supportate da OpenXR per lo sviluppo di realtà mista in Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, realtà mista, MRTK, Mixed Reality Toolkit, realtà aumentata, realtà virtuale, visori di realtà mista, apprendimento, esercitazione, introduzione
ms.openlocfilehash: e622cd617ccf67c0877b9064efe791743e4c34b6
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2021
ms.locfileid: "110333373"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a>Funzionalità supportate da OpenXR di realtà mista in Unity

Il **pacchetto plug-in OpenXR** di realtà mista è un'estensione del plug-in **OpenXR** di Unity e supporta una suite di funzionalità per HoloLens 2 e Windows Mixed Reality visori. Prima di continuare, assicurarsi che il progetto Unity sia [configurato per OpenXR.](openxr-getting-started.md)

## <a name="whats-supported"></a>Attività supportate

Sono attualmente supportate le funzionalità seguenti:

* Supporta le applicazioni UWP per HoloLens 2 e ottimizzare per HoloLens 2 modello di applicazione.
* Supporta le applicazioni VR Win32 per Windows Mixed Reality visore con i profili controller più recenti e la comunicazione remota delle app olografiche.
* Rilevamento della scalabilità globale con ancoraggi e spazio non associato.
* [Ancorare l'API di archiviazione per rendere persistenti](spatial-anchors-in-unity.md) gli ancoraggi HoloLens 2 archiviazione locale.
* [Controller di movimento e interazioni con la mano,](#motion-controller-and-hand-interactions)incluso il nuovo controller HP Reverb G2.
* Tracciamento articolato della mano usando 26 giunzioni e input del raggio delle giunzioni.
* Interazione con lo sguardo fisso HoloLens 2.
* Individuazione della fotocamera foto/video (PV) HoloLens 2.
* Acquisizione realtà mista il rendering del terzo occhio tramite la fotocamera fotovoltaico.
* Supporta ["Play" per HoloLens 2'app Holographic Remoting,](unity-play-mode.md#holographic-remoting-in-unity-editor-play-mode)consentendo agli sviluppatori di eseguire il debug degli script senza compilare e distribuire nel dispositivo.
* Compatibile con MRTK Unity 2.5.3 e versioni più recente tramite il supporto del [provider OpenXR MRTK.](openxr-getting-started.md#using-mrtk-with-openxr-support)
* Compatibile con Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) o versione successiva.
* (Aggiunta nella versione 0.1.3) Supporta [l'app desktop Holographic Remoting](holographic-remoting-desktop.md) da un'app autonoma di Windows compilata e distribuita.
* (Aggiunto nella versione 0.1.4) Supporta il [rilevamento del codice a qr](#qr-codes) in HoloLens2 tramite SpatialGraphNode
* (Aggiunto nella versione 0.2.0) Supporta **l'ancoraggio** nella comunicazione remota olografica
* (Aggiunto nella versione 0.2.0) Supporta i **giunzioni delle mani e il tracciamento della mesh delle mani**
* (Aggiunto nella versione 0.2.0) Supporta **ARPlaneSubsystems per** il rilevamento del piano e posizionare l'ologramma **usando ARRaycastManager.**
* (0.9.0) Supporta **XRMeshSubsystem** e **ARMeshManager** per il mapping spaziale.
* (Aggiunto nella versione 0.9.0) Supporta il plug-in Azure Spatial Anchors SDK per Windows. Per altre informazioni, vedere il progetto di esempio [Mixed Reality + OpenXR Azure Spatial Anchors su GitHub.](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples/tree/main/AzureSpatialAnchorsSample)
* (Aggiunto nella versione 0.9.1) Supporta l'app desktop Holographic Remoting da un'app UWP windows compilata e distribuita.
* (Aggiunto nella versione 0.9.4) Supporta la piattaforma ARM oltre ad ARM64 per l HoloLens 2 applizione.

## <a name="motion-controller-and-hand-interactions"></a>Interazioni con il controller del movimento e la mano

Per informazioni di base sulle interazioni di realtà mista in Unity, visita il manuale [di Unity per l'input XR di Unity.](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html) Questa documentazione di Unity illustra i mapping dagli input specifici del controller a input **più** generalizzabili, il modo in cui gli input XR disponibili possono essere identificati e classificati, come leggere i dati da questi input e altro ancora.

Il plug-in OpenXR di realtà mista fornisce profili di interazione di input aggiuntivi, mappati a **inputFeatureUsage** standard, come descritto di seguito:

| InputFeatureUsage | Controller HP Reverb G2 (OpenXR) | Mano HoloLens (OpenXR) |
| ---- | ---- | ---- |
| primary2DAxis | Joystick | |
| primary2DAxisClick | Azzarre - Clic | |
| trigger | Trigger  | |
| Presa | Presa | Tocco o compressione dell'aria |
| primaryButton | [X/A] - Premere | Simulazione del tocco |
| secondaryButton | [Y/B] - Premere | |
| controllo gripButton | Impugnatura - Premere | |
| triggerButton | Trigger - Premere | |
| menuButton | Menu | |

### <a name="aim-and-grip-poses"></a>Pose mirate e aderenza

È possibile accedere a due set di pose tramite interazioni di input OpenXR:

* Il grip si pone per il rendering degli oggetti nella mano
* L'obiettivo è puntare al mondo.

Altre informazioni su questa progettazione e sulle differenze tra le due posizioni sono disponibili nella specifica [OpenXR - Sottopercorso di input](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).

Le posizioni fornite da InputFeatureUsages **DevicePosition,** **DeviceRotation,** **DeviceVelocity** e **DeviceAngularVelocity** rappresentano tutte la posizione del grip OpenXR.  InputFeatureUsages correlati alle posizioni di aderenza sono definiti in [CommonUsages di](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)Unity.

Le posizioni fornite da InputFeatureUsages **PointerPosition,** **PointerRotation,** **PointerVelocity** e **PointerAngularVelocity** rappresentano tutte la posizione dell'obiettivo OpenXR.  Questi InputFeatureUsages non sono definiti in alcun file C# incluso, quindi è necessario definire inputFeatureUsages come indicato di seguito:

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a>Aptics

Per informazioni sull'uso dell'aptica nel sistema XR Input di Unity, la documentazione è disponibile nel manuale [Unity per Unity XR Input - Haptics.](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics)

## <a name="qr-codes"></a>Codici QR

HoloLens 2 è in grado di rilevare i codici a matrice nell'ambiente attorno al visore VR, stabilendo un sistema di coordinate nella posizione reale di ciascun codice. Per altri dettagli, vedere la documentazione sul rilevamento [del codice a livello](../platform-capabilities-and-apis/qr-code-tracking.md) di codice.  Quando si usa il plug-in OpenXR, afferrare [ `SpatialGraphNodeId` l'oggetto dall'API AR](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) e usare `Microsoft.MixedReality.OpenXR.SpatialGraphNode` l'API per individuare il codice a qr.

Per riferimento, è stato creato un progetto di esempio di rilevamento a livello di codice [in GitHub](https://github.com/yl-msft/QRTracking) con una spiegazione più dettagliata dell'utilizzo per l'API . [ `SpatialGraphNode` ](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs)

## <a name="troubleshooting"></a>Risoluzione dei problemi

Quando si sospende e si riprende un'app Unity HoloLens 2, l'app non può riprendere correttamente, con 4 puntini di rotazione nella visualizzazione HoloLens.

* Impostare **Modalità di invio profondità** su Nessuna **nelle** impostazioni del progetto OpenXR come soluzione alternativa
